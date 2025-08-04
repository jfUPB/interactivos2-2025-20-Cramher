# Unidad 1

## 🛠 Fase: Apply

### Actividad 5: Deconstruccion/Construccion

#### Fase 1: Seleccion

Elegí el sketch que genera módulos circulares dispuestos en una cuadrícula, con orientación aleatoria y un efecto de profundidad controlado por el mouse. Me gusto el ejemplo por la sensacion de profundidad y densidad que me genera ya que juega con el tamaño y la posicion de los circulos.

#### Fase 2: Descripcion

Cuando lo ejecute paso que:

- Se crearon unos circulos de forma ordenada como si fuera una cuadricula.
- Al mover el mouse horizontalmente la candidad de circulos aumentaba volviendo los circulos iniciales mas oscuros como si se estuvieran rellenando.
- Al mover el mouse de forma vertical estos cambiaban de posicion como si fueran conos, dandome una sensacion de profundidad jugando con la posicion de estos.

#### Fase 3: Analisis

El código se puede dividir en las siguientes secciones:

- Parámetros globales: define variables como tileCountX/Y, tileWidth/Height, circleCount, endSize, endOffset.

- setup(): inicializa el lienzo y calcula el tamaño de cada tile.

- draw():

  - Limpia el fondo y fija la semilla aleatoria para mantener la coherencia del patrón.

  - Calcula los valores circleCount, endSize, endOffset en función del mouse.

  - Dibuja una cuadrícula de tiles.

    - Cada tile se traslada y escala.

    - Se rota aleatoriamente en una de 4 direcciones.

    - Se dibujan circleCount círculos desplazados hacia un lado, simulando un movimiento o flujo visual.

- mousePressed(): cambia la semilla aleatoria, produciendo un nuevo patrón.

- keyReleased(): permite guardar la imagen con la tecla s.

#### Fase 4: Convertir

Cuando me puse a experimentar con el codigo me di cuenta que:

- Aumentar tileCountX y tileCountY genera una malla más densa.

- Fijar manualmente circleCount = 10 da un diseño más uniforme.

- Cambiar el rotate() por un ángulo fijo, como rotate(QUARTER_PI), hace que todos los módulos se alineen en diagonal.

- Reemplazar ellipse() por rect() produce un patrón más rígido.

- Agregar strokeWeight() o cambiar stroke() altera la estética.

- Quitar randomSeed() produce un patrón aleatorio diferente cada cuadro.

#### Fase 5: Explorar

[Seleccion modificada](https://editor.p5js.org/Cramher/sketches/bidUapRWT)

Este ejemplo ahora hace:

- Lo mismo que hacia con los circulos pero ahora son cuadrados.

- Cambia la rotacion haciendo clic de manera aleatoria.

- Cambia el color entre negro azul y rojo precionando las teclas 1, 2 y 3.

#### Fase 6: Jugar

Durante este experimento aprendi:

- El uso de nuevas funciones como rect para cambiar la figura.

- Implementar los presskey para poder interactuar mas dinamicamente

- Entender que hay que ajustar los parametros si se quiere cambiar la funcion (hice un ensayo de solo cambiar la funcion ```eliipse()``` por ```rect()``` y no funciono como esperaba ya que se reacomodo todo y dejo mucho espacio sin llenar ahi entendi que tenia que mover un poco mas los parametros).
