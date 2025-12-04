#fotovoltaico 

![[mock-fv.png]]
![[Objetivos Portugal.jpeg]]

**Semana 29J - 2A**
- [x] Introducción de datos fijos de planta (Objetivos) (Back)
- [x] Dato de PR diario - mensual - anual
	- [x] documento en mongo de características de planta *superficie por nave*, rendimiento placa, tipos de placa, edad de las placas, potencia pico
	- [x] llamadas back
	- [x] comparación con el PR de la simulación, desviación del PR
- [ ] Grafico radiación - producción de líneas
Detalles extra:
- [x] Tooltip de los objetivos con el nombre completo de la metrica


**Semana 4A - 9A**
- [ ] Dato de generación perdida cuando la planta esta parada
	- [ ] E_grid - Generada
	- [ ] Cuando se para la planta
	- [ ] Cuanto están rindiendo las placas MODBUS 

Futuro
 - [ ] mqtt consumo - vertido por planta

Tabla de PR:
- [x] De manera mensual y N-12 meses:
- [x] PR calculado
- [x] % de desvío sobre el PR teórico (el teórico igual podemos ignorarlo)
- [x] Que se actualice en base a la planta que se tiene seleccionada
- [x] Darle estilo a la tabla para que quede visual y bien integrada
Energía "perdida":
- [x] Energía teórica - energía real. Es decir, la que se podría haber generado con la radiación acumulada del mes (no la teórica) - la que realmente se ha generado. Habría que hacer también un acumulado mensual con la suma de los diarios, por ejemplo
Esto igual es interesante que vaya en las tarjetas de arriba modo "resumen"
En los gráficos custom de FV:

- [x] Solucionar el problema de redux en los gráficos (parece que va un paso por detrás) de lo que se ha solucionado
- [x] Establecer un tipo de dato para la precarga de los gráficos. Por ejemplo, podemos basarnos en que sea el tipo de dato con código "radiacion_solar_hora_kwhm2" para estandarizar ** He puesto energia activa horaria**

Cambios agosto

- [x] Tarjetas en castellano
- [x] Periodo fijo en las tarjetas (mes en curso)
- [x] Energia perdida en el periodo: = Energia teorica por irradiacion - generada
- [x] Quitar el porcentaje de PR
- [x] Arreglar el grafico incompleto de autoconsumo

PENDIENTE
- [x] Meter una tabulación a los dispositivos hijo en el desplegable de la selección de activos para que quede clara la jerarquía
- [ ] Grafico modular solo necesita fecha de inicio
- [ ] Errores de calculo mas detallados
- [ ] Mejora de los selectores de dato - tipo de dato
- [x] Tarjeta de PR
- [x] cargar consumo mensual
- [x] poner las que dan fallo primero
- [x] responsibidad del dashboard según ancho
- [x] energia perdida por planta
- [x] En gráficos que la fecha actual se situe en un dia mas y la hora a 00
- [x] Los valores anomalos de pr se ignoran y aparecen marcados como no validos en la lista por mes.
- [x] Botón de descarga en dashboard.
- [ ] Meter null (no undefined en los graficos)
- [x] tiene sentido el health por debajo en los que se muestran como source?

## Semana 7Octubre - 11Octubre
- [x] Expandir el path y los errores de cada nodelink
- [x] Icono de warning en el pr si alguno de los mensulaes está fuera de rango
- [x] En graficos los graficos se ajustan a la zona horaria del usuario 7/10/24
- [x] Bolitas en cada NodeLink con sus Health
- [x] Enlaces a Watch?
- [ ] Disponibilidad sobre las horas totales: cuantas horas ha estado generado mientras había radiación por hora
- [x] Serie temporal de horas de actividad por cada inversor
- [x] Navegación por UUID para watch de FV
- [x] Ordenar display de errores de PR
- [x] Alarma de PR??
- [x] Añadir símbolo de anti-vertido
- [x] ALERTA DE PR Y ANTIVERTIDO  
- [x] Poner primero las que tengan error en watch   
## Reunión 18/10/2024
- [ ] Informe mensual de los datos de generación fotovoltaica de todas las plantas y de cada planta. -> Informes. Informe de disponibilidad
- [x] Icono de aviso de pr solo para el ultimo mes o objetivo quitarlo cuando se aplique corrección
- [x] *** [2] Si en fotovoltaico hay un icono con error mostrar que el elemento es un trafo, inversor o fotovoltaico
- [x] Poner como warning (amarillo) todos los nodos que tengan errores pero >0% de comunicaciones. Posiblemente hacerlos por perfil. 
## Reunión 25/10/2024
- [x] Llamada a miguel saguesa para saber la eficiencia de los inversores para la energía perdida
- [ ] Perdida de energía prisma (Iker)
- [ ] Alarma general que se está generan menos de lo esperado en plantas sin antivertido
- [x] *** Si hay un pr menor de lo esperado añadir un aviso de pr en la zona derecha. Mes en curso y anterior.
- [x] *** Buscar forma de comprobar si un dispositivo que está comunicando no esta generando los datos que debe, a pesar que el inversor y la placa aparentemente estén funcionando bien.
- [x] *** [1] Servicio general de traducción de tipos de dato y agrupación.
	- [x] Parcialmete se ha traducido cada parte, falta un servicio central.
- [x] Ocultar los warnings según rol en watch
- [x] Falta saber que rol es el que tiene que tener
- [x] Los graficos con codigo "" se agrupan y no deberian
- [x] Los health con ok:0 y nok:0 tienen que tratarse como desconectado
- [x] selector de columnas y barra de alarmas solo para los usuarios que tengan permisos de watch-dev
- [x] Los concentradores tienen color según conectionState

## Reunión 08/11/2024
- [x] Parece que "798e9dd3-04c7-448b-a385-505134463a21" no tiene nombre.
- [ ] *** Hay que arreglar la energía perdida para que se refleje cuando una planta ha estado completamente sin conexión.
- [ ] Líneas que marca el consumo y barras que marcan que es vertido y que se usa de la red.
- [x] En las plantas antivertido en la tabla de PR se podrían compara las plantas sin antivertido con las que tienen antivertido. En la planta con antivertido comparar cuanto se pierde respecto al valor teórico.
- [x] Informe anual con todos los eventos y la energía perdida por esos fallos.
- [x] Descartar datos de Portugal donde había antivertido.
- [ ] Comparar los datos relativos a los objetivos para observar si hay problemas.
- [x] Botón descartar anti vertido ???
- [x] Falta la energía excedente
- [ ] % de disponibilidad de la planta
- [x] Los iconos de ok de watch no tienen que salir si la ultima conexión es hace demasiado tiempo

## Reunión 08/11/2024
- [ ] Modo nocturno
- [x] Comparativas de plantas en base a un dato concreto, le hacen falta la lista de alarmas,
- [x] Dashboards meter el componente desde
- [x] Grafico de área
- [x] En el back sacar los uuid de los tipos de dato

## Reunión presencial
- [x] Los gráficos se montan unos encima de otros
- [ ] Tema oscuro intercambiable, pero no negro absoluto.
- [x] ***Producción -> Consumo -> Autoconsumo -> Vertido -> Antivertido -> perdida -> radiación -> co2 + arboles.
#### Consumo eléctrico
- [x] **Hay que revisar que consumo no tenga también el autoconsumo, habría que descontar la energía producida porque es redundante**.
- [x] Barra roja en el grafico de autoconsumo que divide la parte de consumo de la red y la parte de consumo exterior
- [x] Hay que diferenciar entre consumo eléctrico y energía inyectada.

- [x] Cuando se pone pantalla completa se pierde la planta seleccionada.
- [x] Energía perdida -> Energía perdida total
- [x] En la grafica de autoconsumo hay que poner una ralla que marque el autoconsumo y columnas que marquen: producción fotovoltaica, vertido e inyección.
- [ ] Meter 0.5 de degradación anual.
- [ ] Meter los powermeter en link.
- [x] ***Los tipos de dato del grafico de fotovoltaico en orden alfabético.
- [ ] Agregar las plantas que tengan fotovoltaico al informe de plantas.
- [ ] En planatas con antivertido sumar su energía perdida y mostrarla en algún sitio. 
- [x] *** Ordenar las plantas según PR y antivertido

## 29/11/2024
Marcar plazos para alarmas URGENTE.

### 13/12/2023
- [x] Mandar esquema de como se muestra la energía perdida-generada-nuevo.
- [x] Disponibilidad de la instalación.
- [ ] Excell con los datos de últimos 12 meses y mes en curso.
- [x] Error de disyuntor.
- [x] Preparar estructura de mostrar las alarmas.      

### Prioridades 2025
- [x] Comenzar alarmas
- [ ] Degradación en el back de los paneles
- [x] Varias plantas en el grafico de fv
	- [x] El grafico modular de fv cambia bien pero hay que modificar el "Todas" del selector
	- [ ] Añadir selector de todo?
- [x] Energía vertida al mes por planta
- [x] Energía perdida por planta al mes
- [x] Energía perdida por antivertido por planta al mes


La descarga de informes no funciona, descargar el informe en vez de descargar.


### 11/02/2025
- [ ] Revisar la disponibilidad de los inversores
- [ ] Poner a 0 los valores negativo del grafico de autoconsumo
- [ ] El grafico de objetivos tiene 0 para 2025

### 25/02/2025
- [ ] quitar decimales de las tarjetas
- [ ] kwhm2 en medida de radiación
- [ ] El botón de intro objetivos elimina la línea
- [ ] Objetivos en 2 líneas y que aparezca que el mes esta prograteado, que el objetivo es del bussiness plan
- [ ] COMPROBAR TODA LA TABLA DE OBJETIVOS
- [ ] Cambiar PR a los últimos 12 meses en vez de mes en curso
- [ ] Falta febrero en la lista de antivertido
- [ ] Porcentaje de objetivos en las tarjetas