Piden los datos de neo4j en forma de Fabrica-Dispositivo-Dispositivo
[Sharepoint](https://dominionglobal.sharepoint.com/teams/TRACONE/Documentos%20compartidos/Forms/AllItems.aspx?id=%2Fteams%2FTRACONE%2FDocumentos%20compartidos%2FProyectos%2FEjecuci%C3%B3n%2FGDPR23%2D00025%20%2D%20PROYECTO%20I%2BD%20CEINDUS&viewid=951879fb%2De14f%2D4a86%2Dacfe%2Dcb6d903e5dad)

### 07/03/2024
- Comunidades energéticas industriales que tienen sistemas de generación-consumo propios.
- Aprovechar la flexibilidad de los recursos
- Sistemas de generación de claor/frio 
- OBJETIVO: Conjunto de soluciones para gestionar los recursos energéticos
	- Obj1: Optimizador energético: Consumos flexibles, mas autoconsumo
	- Obj2: Que la comunidad opere de forma aislada
	- Obj3: analizar si se pueden dar servicios a terceros
	- Obj4: Investigar una herramienta para el análisis prospectivo a largo plazo
Paquetes de trabajo:
(captura)
- PT1 Gestión - difusión
- PT2 Especificación de solución
#### Revisión de 2023
Prorroga hasta marzo, justificación en Abril.

- [ ] Hay que hacer publicidad del proyecto en las web (PT1)
- [ ] Análisis de las CEI (Resp de DOMINION)
	- [ ] Aspectos regulatorios
	- [ ] Existentes
- [ ] Entregable 2.1 

#### Justificación
- Solicitud de continuación
- Justificación de la ejecución del proyecto
Importante justificar la difusión del proyecto y las subcontratas
- [ ] Que trabajos se han realizado
- [ ] Impacto del I+D
- [ ] Incidencias para justificar la prorroga
- [ ] Fotos del cartel con el link a la pagina web y que se ve en la web
FECHA LIMITE 12 ABRIL

Reuniones de seguimiento cada 3 meses

### Reunión 15/03/2024

En un lado se llama prensa y en otro se llama línea prensa, pero son lo mismo.
En Gonvarri las prensas no tienen tipos
Sacar nombres de cada maquina y su nivel
assetgroup->puesto->maquina
despues de lineas prensa hay que generar un nivel mas que agrupe las prensas , uno para lineas de corte, 
Necesitan datos de consumo por elemento, datos quartohorarios, los pasamos por UUID de elemento pero hay un id de series temporales.

### 21/11/2024
Plataforma de gestamp, han hecho el árbol de las líneas de producción, con los datos hacen benchmark.
Periodo de entrenamiento de 90 días óptimos.
En el proyecto la herramienta se adapta al servicio pero el desarrollo previo ya esta hecho, hay una licencia.
Sacar datos de planta para conocer la planificación de producción y estimar el consumo.
**Pasarles otras plantas o líneas con datos mas constantes.**

### 13/12/2024
Comparativa de dias, porque x dia se diferencia respecto al mas parecido, al que mas se ha consumido y al que menos.

Preguntar por IP para que nos den acceso desde aqui.

### 31/01/2025
http://150.241.8.240:8084/NaiaRestApi-preproduccion/resources/benchmarksservice/factory/evaluation/?cod_planta=GON&dia=2024-04-03

*URGENTE*
Necesitan saber que acometidas tenemos, los trafos de que acometidas cuelgan, y que maquinas dependen de cada trafo.
Y potencia contratada por acometida. Lo necesitan para el análisis de picos.

Quieren hacer una planificación del consumo en base a la producción. Necesitamos otra línea parecida a la de Galicia.

### 28/02/2025
La idea es que nos pasan un docker con el código.
Un socio no va a poder justificar todo lo que había pedido en un principio.

