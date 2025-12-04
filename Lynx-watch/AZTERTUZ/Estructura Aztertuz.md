---
tags:
  - aztertuz
  - backend
  - frontend
  - tareas
---

## Ordenes de trabajo

Almacenadas en Mongo, desencadenadas por una alarma de un dispositivo:
Dispositivo -> Alarma -> OT

Hay que tener en cuenta que puede ser que se complete la reparación o no haga falta y se esta se ignore. Seria conveniente poner un límite de tiempo para pasar a ignorada, un poco como cuando caducan las issues de github.
```json
<Orden>{
	_id: IdMongo/UUID,
	estado: "NUEVA"|"ASIGANDA"|"COMPLETADA"|"IGNORADA",
	fechaIncidencia: Date,
	problema: string,   
	source: UUID,
	gravedad: TipoGravedad, // o urgencia
	fechaArreglo?: Date, // opcional
	operarioResponsabe: UUID/Nombre, // quien lo tiene asignado, para que aparezca en el dashboard
	anotaciones: Anotacion[], // antes de completarse o asignarse	
	completada: {
		fecha: Date,
		operario: UUID,
		horas: number,
		anotaciones: Anotacion[]
	}
}

<Anotacion>{
	fecha: Date,   
	usuario: UUID,
	mensaje: string
}
```

### Tabla de reglas

Se plantea la opción de meter en el NiFi para que cuando se consuma un valor, se comprueba según las reglas y se genera una OT. En principio Aitor da el visto bueno pero hay que diseñar la implementación.
```json
{
	regla: string,
	sources: string[], // sources en los que se aplica
	periodos: [Date,Date][], // periodos en lo que se aplica
	gravedad: TipoGravedad,
	condicion: formula, // para combinar gravedad+fecha 
}
```

### Servicio para las alarmas

Este servicio es posiblemente un poco especifico para nuestro caso de uso, se podrán hacer modificaciones

``` ts
/*
* He definido los argumentos como un tipo que puede estar incompleto porque 
* venia bien para actualizar estados anteriores. La primera carga debera ser
* completa 
*/
type ArgsQueryAlarmas = {
  first?: number | null,
  offset?: number | null,
  source?: string | null,
  register?: string | null,
  from?: number | null,
  to?: number | null
}

/*
* El servicio de alarmas mantiene un estado que se actualiza según se 
* llama a loadAlarmas, la idea es ir actualizando los argumentos para 
* modificar los sources y fechas. Añadí un campo seleccionFechas para 
* diferenciar cuando se ha elegido un periodo manualmente y pausar la 
* actualizacion automatica
*/
interface AlarmasService {
	estadoAlarmas$: BehaviorSubject<EstadoAlarma>;
	loadAlarmas: (args:ArgsQueryAlarmas & {
		seleccionFechas?: "AUTOMATICA" | "MANUAL" 
	}) => void;
	
}
```


```js
query GetPeriodosErrorCalculado($solarGroups: [String], $from: Float, $to: Float, $codigoTipoDato: String, $umbralError: Float) {
  getPeriodosErrorCalculado(solarGroups: $solarGroups, from: $from, to: $to, codigoTipoDato: $codigoTipoDato, umbralError: $umbralError) {
    solargroup
    sources {
      dispositivo
      source
      periodos {
        alarmLevel
        //aggregateIntervalByCodigo
        from
        register
        to
        state
      }
    }
  }
}
---
{
  "solarGroups": ["d26878ce-9b82-4324-8f82-57cbc16d842c",
  "4f80e9ab-7509-4202-9ebb-01a28adfd74e"],
  "from": 1744467780000,
  "to": 1749738180000,
  "codigoTipoDato": "energia_fv_perdida_teorica_kwh_hora",
  "umbralError": 200
}
```

Información por inversor (mas cosas en el cliente de Apollo)
```js
query Query($uuid: String) {
  findSource(uuid: $uuid) {
    modelo
    nombre
    silenciado
  }
}
```

## Cell
### Interfaz servicio de WS "Cell"
Servicio de estados de conexión.
Las funciones publicas son subscribe y unsubscribe, se consumen desde la suscripción de subscribe o buscando en $subjects, la función subscribe() debe comprobar si hay una entrada en $subjects.

```ts
// T es el payload del socket, en este caso CellPayload.
interface WSService<T> {
	// Lista de sources con una subscripcion activa (idealmente no se consume directamente)
    $subjects: Map<
        string,
        {
            subject: BehaviorSubject<T | undefined>;
            count: number;
        }
    >;
	// Llamada para suscribirse desde un componente
	// Devuelve el observable
    subscribe: (input: string) => Observable<T | undefined>;
    // Llamada para desuscribirse de forma normal
    unSubscribe: (input: string) => Promise<boolean>;
}

```

Estructura paquete de CELL
```typescript
export type CellPayload = {
  uuid: string // uuid del NodeLink
  time: number // Fecha de emision
  healths: CellHealth[] // Elemntos por debajo que dan error
  connectionStates: ConnectionState[] // Elementos por encima que dan error
  alarmResults: AlarmResult[] // Alarmas (wip)
  lastChange: number // hora del cambio de estado
}

// Estado de los intentos de conexion al source, undica cuando paquetes se han devulto como ok/nok en el periodo de tiempo from-to y si se han reportado errores.
export type CellHealth = {
  uuid: string
  ok: number
  nok: number
  from: number
  to: number
  errors?: string[]
}
  
// Estado de las conexiones hacia el source.
export type ConnectionState = {
  uuid: string
  // Conexion por mqtt a mosquitto  
  connection: boolean
  // Estado de la conexion con el source
  state: boolean
}

// No afecta.
export type AlarmResult = {
  time: string
  source: string
  register: string
  level: string
  value: string
}
```
### Ejemplo de un paquete de CELL
Healths hace referencia al estado de la conexión con el propio dispositivo (si coincide el uuid como aquí)
ConnectionStates hace referencia a la conexión con otros dispositivos (state) o el broker mqtt (connection)
En este caso se esta obteniendo información de "d43934bf-b068-48bb-afc9-6e3dabf433d1"
que tiene un health sobre la conexión hacia él mismo y cuando se hizo esa comprobación y 2 connectionStates, el primero indicando que la conexión MQTT es correcta y el segundo indicando que tiene un dispositivo dependiente con conexión correcta.
"time" es el insatante de actualizacion en el broker aunque no haya cambios.
"lastChange" es el ultimo cambio en el broker.
```json
  
{
	"time": 1750922080940,
	"uuid": "d43934bf-b068-48bb-afc9-6e3dabf433d1",
	"healths": [
	{
		"ok": 5,
		"nok": 0,
		"from": 1750921860005,
		"to": 1750921980009,
		"uuid": "d43934bf-b068-48bb-afc9-6e3dabf433d1"
	}
	],
	"connectionStates": [
	{
		"uuid": "d43934bf-b068-48bb-afc9-6e3dabf433d1",
		"connection": true
	},
	{
		"uuid": "407d0f09-02b0-4504-80c7-d9f756a7a52e",
		"state": true
	}
	],
	"alarmResults": [],
	"lastChange": 1750903378883
}
```
### Interfaz de servicio de datos de alarmas y GMAO
Define como se accede a los datos en MongoDB, se asume que update Datos actualiza $datos a parte de devolver el nuevo valor

TODO: Para un dispositivo devolver toda la información de alarmas y OTs

```ts
/*
* (Todavia en desarrollo, pendientr de implementar en los servicios actuales, se 
* puede modificar)
* T -> para el dato recibido del back
* P -> para los parametros de busqueda
*/
interface ConsultasPeriodicasService<T,P> {
	$datos: Subject<T>
	parametrosUltimaConsulta: {
		utlimaActualizacion: Date
	} & P
	updateDatos(params:P): T
}
```

Ejemplo de un periodo de error:
``` json
{
	"alarmLevel": 350,
	"calculoPeriodo": null,
	"from": "2025-05-25T06:17:24.596Z",
	"register": "a8f59ad3-6f32-4da5-870a-032ff3fb7c88",
	"to": "2025-05-25T06:17:24.596Z",
	"state": "350"
},
```

### Servicio para obtener la información de los register
Tener en cuenta que los register representan los tipos de dato que emite un dispositivo e indica el nombre, descripción y unidades, no los valores. 

Para sacar los datos de los nodelinks, registers y tipos de dato he creado un servicio que además de solicitarlos al back los cachea para reusarlos si ya los has pedido antes.

Los register y tipo de dato representan practicamente lo mismo, pero un register está asociado a un enlace nodelink-tipodato, yo tampoco entiendo el motivo de que estén separados.

```ts
interface LinkService {
	getNodeLink(uuid:string): NodeLink | undefined
	getRegister(uuid:string): Register | undefined
	getTipoDato(uuid:string): TipoDato | undefined
}
```

Incluir como se accede a la información del register para saber el tipo de error.
El visor va a tener también la energía perdida .