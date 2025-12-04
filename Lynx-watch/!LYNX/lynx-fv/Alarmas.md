``` cypher
query FindStateInterval($first: Int, $offset: Int, $source: String, $register: String) {
  findStateInterval(first: $first, offset: $offset, source: $source, register: $register) {
    alarmLevel
    channel
    field
    register
    source
    state
    from
    to

  }

}
---
{
  "first": 4,
  "offset": null,
  "source": null,
  "register": null
}
```

- channel
- field: CONCENTRADOR
- register: tipo dato
- source: dispositivo

![[alarmas.png]]

### Niveles de alarma
0: OK (verde)
1-99: Info, hay que revisar pero no para el equipo (azul)
100-199: Warning, Hay que revisar  (amarillo)
200-299: Minor, fallo del equipo, menor rendimiento (naranja)
300-399: Major, fallo critico (rojo)

## TODO:
- [ ] Descargar excel
- [ ] Separar columna de energia vertida