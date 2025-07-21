# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 1: Diseño y Arte generativo

#### Diseño Generativo:
El diseño generativo es una forma de generar imagenes a travez de patrones y parametros que van cambiando en tiempo real. Estos pueden cambiar segun su posicion dentro de la pantalla junto con los dibujos o figuras que se tengan.

#### Arte generativo
El artes generativo es una forma de expresion en cuanto a lo que se quiere con un orden y padron especifico para lograr la profundidad y detalle que se busca de una obra de arte. Este busca transmitir algun sentimiento por medio de sus patrones, colores y aleatoriedad que le brinda la generacion de este.

#### Diferencias entre el diseño y el arte generativo
Mientras que el diseño generativo tiene unos parametros ya establecidos y una dorma de ser generado, el arte busca usar varios patrones y ser un poco mas libre para cumplir con su objetivo. De modo que se puede usar diseño generativo para hacer arte generativo pero no se puede usar arte generativo para hacer diseños generativos.

#### Posibilidades ofrecidas a mi perfil profesional
Mayor libertad a la hora de diseñar una experiencia, pues concidero que esta me puede abrir un mundo de posibilidades en cuanto a lo que entretenimiento digital en tiempo real se refiere.

### Actividad 2: Proyeccion de Ingeniero en Diseño de Entretenimiento Digital

#### ¿Que hace un IDED?
Siempre he conciderado que alguien enfocado en experiencias interactivas busca mejorar la expereciencia para las personas dentro de otras formas de entretenimiento, mas concretamente que te ayude a interactuar con lo que esta pasando a tu alrededor brindando otra perspectiva de lo que esta pasando.

#### Potencial experiencias inmersivas colectivas
Si en un concierto un artista se encarga de conectar al publico a traves de su musica, poder acompañar todo esto con una visual que de a entender lo que esta diciendo el artista o transmitir sentimientos que no se logran plasmar en palabras el publico enloqueceria aun mas y seria una mejor experiencia para ellos.
Si en un museo el autor busca cautivar a sus espectadores, que pasaria si en una sola experiencia la obra cobrara vida y contara la historia que el autor queria transmitir.
Creo que no hay limite para lo que se puede hacer con una experiencia inmersiva colectiva ya que se puede usar en cualquier ambito de nuetras vidas y de tener exito nos permitira sentir mas.

#### Vision profesional
Si tengo que escoger algo relacionado con esto, creo que me interesaria mucho trabajar en conciertos para que los artistas puedan llegar mas a su publico, pese a que ya hay artistas que lo logran a veces peude ser dificil conectar con tanta gente y tenerlos pendientes del espectaculo. Considero que se podria aprovechar mucho mas si algo visual captara su atencio sobretodo para aquellos mas distantes del escenario.

### Actividad 3: Exploracion de Referentes

#### Ejemplo Seleccionado
```js
'use strict';

var count = 0;
var tileCountX = 6;
var tileCountY = 6;

var drawMode = 1;

function setup() {
  createCanvas(windowWidth, windowHeight);
  rectMode(CENTER);
  noFill();
}

function draw() {
  background(255);

  count = mouseX / 20 + 5;
  var para = min(height, mouseY) / height - 0.5;

  var tileWidth = width / tileCountX;
  var tileHeight = height / tileCountY;

  for (var gridY = 0; gridY <= tileCountY; gridY++) {
    for (var gridX = 0; gridX <= tileCountX; gridX++) {

      var posX = tileWidth * gridX + tileWidth / 2;
      var posY = tileHeight * gridY + tileHeight / 2;

      push();
      translate(posX, posY);

      // switch between modules
      switch (drawMode) {
      case 1:
        translate(-tileWidth / 2, -tileHeight / 2);
        for (var i = 0; i < count; i++) {
          line(0, (para + 0.5) * tileHeight, tileWidth, i * tileHeight / count);
          line(0, i * tileHeight / count, tileWidth, tileHeight - (para + 0.5) * tileHeight);
        }
        break;
      case 2:
        for (var i = 0; i <= count; i++) {
          line(para * tileWidth, para * tileHeight, tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(para * tileWidth, para * tileHeight, -tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(para * tileWidth, para * tileHeight, (i / count - 0.5) * tileWidth, tileHeight / 2);
          line(para * tileWidth, para * tileHeight, (i / count - 0.5) * tileWidth, -tileHeight / 2);
        }
        break;
      case 3:
        for (var i = 0; i <= count; i++) {
          line(0, para * tileHeight, tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(0, para * tileHeight, -tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(0, para * tileHeight, (i / count - 0.5) * tileWidth, tileHeight / 2);
          line(0, para * tileHeight, (i / count - 0.5) * tileWidth, -tileHeight / 2);
        }
        break;
      }

      pop();

    }
  }
}

function keyReleased() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
  if (key == '1') drawMode = 1;
  if (key == '2') drawMode = 2;
  if (key == '3') drawMode = 3;
  if (keyCode == DOWN_ARROW) tileCountY = max(tileCountY - 1, 1);
  if (keyCode == UP_ARROW) tileCountY += 1;
  if (keyCode == LEFT_ARROW) tileCountX = max(tileCountX - 1, 1);
  if (keyCode == RIGHT_ARROW) tileCountX += 1;
}
```
#### Explicacion Ejemplo Seleccionado
El codigo permite interactuar con la densidad de las lineas dibujadas y la rotacion de estas todo a traves de la posicion del mouse en la pantalla de interaccion. Si el mouse se desplaza horizontalmente se dibujan mas o menos lineas, si se desplaza verticalmente, las lineas dibujadas son rotadas para cambiar de posicion.

#### Ejemplo Modificado

```js
'use strict';

var count = 0;
var tileCountX = 6;
var tileCountY = 6;

var drawMode = 1;

function setup() {
  createCanvas(windowWidth, windowHeight);
  rectMode(CENTER);
  noFill();
}

function draw() {
  background(255);

  count = mouseX / 20 + 5;
  var para = min(height, mouseY) / height - 0.5;

  var tileWidth = width / tileCountX;
  var tileHeight = height / tileCountY;

/// Esto concretamente, cambio de color segun la posicion del mouse
  let r = map(mouseX, 0, width, 50, 255);
  let g = map(mouseY, 0, height, 50, 255);
  let b = map(mouseX + mouseY, 0, width + height, 100, 255);
  stroke(r, g, b, 150);

  for (var gridY = 0; gridY <= tileCountY; gridY++) {
    for (var gridX = 0; gridX <= tileCountX; gridX++) {

      var posX = tileWidth * gridX + tileWidth / 2;
      var posY = tileHeight * gridY + tileHeight / 2;

      push();
      translate(posX, posY);

      // switch between modules
      switch (drawMode) {
      case 1:
        translate(-tileWidth / 2, -tileHeight / 2);
        for (var i = 0; i < count; i++) {
          line(0, (para + 0.5) * tileHeight, tileWidth, i * tileHeight / count);
          line(0, i * tileHeight / count, tileWidth, tileHeight - (para + 0.5) * tileHeight);
        }
        break;
      case 2:
        for (var i = 0; i <= count; i++) {
          line(para * tileWidth, para * tileHeight, tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(para * tileWidth, para * tileHeight, -tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(para * tileWidth, para * tileHeight, (i / count - 0.5) * tileWidth, tileHeight / 2);
          line(para * tileWidth, para * tileHeight, (i / count - 0.5) * tileWidth, -tileHeight / 2);
        }
        break;
      case 3:
        for (var i = 0; i <= count; i++) {
          line(0, para * tileHeight, tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(0, para * tileHeight, -tileWidth / 2, (i / count - 0.5) * tileHeight);
          line(0, para * tileHeight, (i / count - 0.5) * tileWidth, tileHeight / 2);
          line(0, para * tileHeight, (i / count - 0.5) * tileWidth, -tileHeight / 2);
        }
        break;
      }

      pop();

    }
  }
}

function keyReleased() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
  if (key == '1') drawMode = 1;
  if (key == '2') drawMode = 2;
  if (key == '3') drawMode = 3;
  if (keyCode == DOWN_ARROW) tileCountY = max(tileCountY - 1, 1);
  if (keyCode == UP_ARROW) tileCountY += 1;
  if (keyCode == LEFT_ARROW) tileCountX = max(tileCountX - 1, 1);
  if (keyCode == RIGHT_ARROW) tileCountX += 1;
}

```

#### Explicacion Ejemplo Modificado
Ahora el ejemplo sigue funcionando igual solo que ahora cambia de color las lineas dibujadas y el color se hace mas pronunciado segun la cantidad de lineas dibujadas determinadas por la posicion del mouse.













