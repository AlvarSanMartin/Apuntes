#imasd #externo
## Contexto
El sonar devuelve n intensidades por rayo, implica cierta dificultad en la extracción de features.
Hay una distorsión por el movimiento del vehículo.
Se tarda segundos (5-10s) para hacer un scanner 360
Doppler velocity log -> estimar la velocidad
Es complicado el uso del sonar para extracción de features porque
*stochastic maps* Para comparar las fetures entre estados, teniendo en cuenta el movimiento
Problema del sonar2D, y como hay que establecer distancias por lectura.
El robot necesita dar varias vueltas para completar el escaneo.

El sonar genera una nube de puntos en un plano, usan CFAR para convertirlo en una nube de puntos real.

### Añadir
Intentar poner que se ha añadido un giroscopio en el robot para 