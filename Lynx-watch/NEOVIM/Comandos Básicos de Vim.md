`[] Simboliza el cursor`
## 1. Básicos
#### Inserciones
`i` Insertar antes del cursor
`I` Insertar al principio de la línea

`a` Append después del cursor
`A` Append al final de la línea

```
  O
Ii[]aA
  o
```
`o` Open línea abajo
`O` Open línea arriba

`c[n]{motion}` Eliminar + Insertar hasta n motions ej.: `c3w` corta hasta dentro de 3 palabras y se pone en modo *Insert*

`cw | ce` Elimina el resto de la palabra `w` o hasta el principio de la siguiente `e`
#### Movimientos
```
gg <-Inicio de archivo

  ^
<hjkl>  {caracteres}[hjkl]
   ⌄
   
Esto es un [t]exto-Ejemplo de prueba
^                ^ ^     ^ ^       ^           
0                e w     E W       $

{n}G | :{n} <- A la linea {n} del archivo
G <- Fin de archivo
```

`w` Al principio de la siguiente palabra
`e` Al final de la palabra actual

`W | E` Hacen lo que `w | e` pero ignoran caracteres especiales y buscan el espacio blanco 

`b | B` Al principio de la palabra anterior, en mayus ignoran caracteres epeciáles

`0` Primera columna
`^` Primer carácter no blanco

#### Copia-Pega

`y` Yank - copiar
`yy` Copiar la línea
`p` Pegar

`x` Eliminar carácter (No copia como d)
`d` Delete (Cortar en realidad)
`dd` Cortar la línea

`u` Undo-deshacer
`ctrl-r` Redo-rehacer

#### Búsqueda

`/{plabra}intro` Busca la palabra `n` para la siguiente y `N` para la anterior

## 2. Mejoras a lo básico

`[n].` Repite el último comando, no se incluyen movimientos pero si escritura de caracteres. Puede lanzarse n veces.

`%` te mueve entre pares: `[]{}()`
`* | #` Te mueve a la siguiente `` o anterior `#` palabra en la que está el cursor.

`{desde?}[gU | gu]{hasta}` Para pasar un fragmento de texto a mayúsculas o minúsculas respectivamente 

**Estructuras**

Estructura desde - hasta
`{posicion inicial?}{comando}{posicion final}`
`0y$` Desde el inicio de la línea hasta el final


**Una línea avanzado**

```
  let a = arr.map(e => ({a:1,b:e}))  
^ ^    ^^                      ^  ^  ^
0 ^   t= f=                   2fe g_ $
```

`t{char} | f{char}` Para posicionarse antes y encima del carácter que se busca con `, | ;` se avanza y retrocecede.