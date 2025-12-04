#fotovoltaico 
#lynx 

Esquema:[[Esquema Nodos.canvas|Esquema Nodos]]
Tareas: [[!LYNX/lynx-fv/TODO|TODO]]
# 1. Exploración
Búsqueda en una planta de sus grupos solares
```cypher
match (f:Fabrica {nombre:"Temporal"})-[]->(s:Solar) return f,s
```

Búsqueda de inversores
```cypher
match (f:Fabrica {nombre:"Temporal"})-[]->(s:Solar)-[]->(ss:Solar)-[:ESTRUCTURA]->(t)-[]->(datos:Dato) return f,s,ss,t,datos
```

# 2. Obtención de datos

## Inversor
Generación de energía de una planta fotovoltaica.
```json
{
  "uuid": "965ef02f-ecbf-45c3-8943-6de99c22a086"
}
```
- Energía generada (kWh) por hora/día/mes.
- Energía generada en total.
Output
- Output Active power (W)
- Output Aparent power (Preguntar diferencia)

## Transformador
```json
{
  "uuid":"f0ae5c30-9ae7-43a6-a300-3bbb55d21192"
}
```
Solo corriente alterna, esta en el limite de la planta, controla la entrada-salida de energía.
Valores comunes:
- Frecuencia
- Intensidad
- Corriente
- ...
Consumo (exterior):
- Por hora/día/mes (kWh)
- Hay un campo extra consumo_energia

Generación (FV):
- No hay datos de salida

# Contadores
Controlan la entrada a la fabrica, no hay datos de exportada.
Parece que suma el consumo de los transformadores
```json
{ 
  "uuid":"d00327de-0c99-4d5d-b611-101589395eb4"
}
```

## Resumen métricas
- **Energía activa:** Consumida por la planta total?