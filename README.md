# Laboratorio 1 - "Trayectorias, Entradas y Salidas Digitales"

***INTEGRANTES***

* Marco Antonio Quimbay Dueñas
* Felipe Chaves Delgadillo

## Descripción Solución Planteada
Se comenzó con el ***diseño de la herramienta***, considerando diversos aspectos cruciales. Esto incluyó dimensiones precisas del marcador, la geometría y dimensiones del soporte del efector final, el espacio adicional requerido para el resorte, el ángulo de la superficie, así como diversas tolerancias, como las relacionadas con los roscados y la relacionada a la manufactura aditiva. Además, se abordaron otros aspectos importantes, como la distribución de esfuerzos mediante el suavizado de superficies, entre otros.

Adicionalmente, siguiendo las sugerencias del profesor, se optó por diseñar la herramienta con un ángulo de 45°. Esta decisión se tomó con el fin de facilitar el acceso a la superficie y evitar posibles la concordancia de los sistemas coordenados, obteniendo mediante el modelado en fusion 360, el siguiente modelo de la herramienta:

[INSERTE IMAGEN DEL MODELO DE LA HERRAMIENTA]

Después de su impresión en 3D y de ensamblar todas sus partes, la herramienta exhibió la siguiente apariencia:

[INSERTAR FOTO DE LA HERRAMIENTA IMPRESA]

Una vez completado el diseño de la herramienta, se procedió al modelado del objeto de trabajo con el fin de preparar la creación de la trayectoria deseada. Se cumplió con los requerimientos de incluir el nombre y logotipo de la empresa conocida "GitHub", así como las iniciales de los nombres de los miembros del grupo "MQFC". Para esto, se consideraron las dimensiones y ángulos de inclinación del tablero sobre el que se iba a dibujar proporcionados por el monitor del curso. El modelo resultante fue creado utilizando el software Inventor 2024.

[INSERTAR IMAGEN DEL WORKOBJECT]

Posteriormente, se procedió a la inserción y configuración del controlador y del robot manipulador IRB 140 en el software RobotStudio; Se creó el sistema de coordenadas del TCP (Tool Center Point) mediante la inserción del modelo previamente diseñado de la herramienta. Se definió el sistema de coordenadas en la punta de la herramienta, donde se esperaba que estuviera la punta del marcador. Después, se llevó a cabo la ubicación y alineación precisa de la herramienta, asegurando que su base y alineación coincidieran con el soporte para herramientas del robot.

A continuación, se añadió el modelo que incluía el logo y las letras para definir el WorkObject. Se estableció la ubicación y orientación del WorkObject considerando que su eje z coincidiera con la orientación necesaria del TCP durante la ejecución de la trayectoria.

Para la generación de las trayectorias se definieron diversos puntos clave al rededor de los símbolos a dibujar, añadiendo algunos puntos un poco alejados de el area del dibujo para poder desplazarse entre letras, y usando el tipo de movimiento linear (MoveL) con una velocidad de v50 mm/s y un zone de zfine. 

Adicionalmente, es importante destacar que, en algunas ocasiones al definir los puntos para las trayectorias, el programa generaba cambios en las orientaciones del robot, posiblemente debido a su posición actual durante la definición. Esto resultaba en giros bruscos del robot, lo que a su vez provocaba problemas de singularidad. Para resolver este inconveniente, fue necesario ajustar las configuraciones modificando los cuadrantes de los targets predefinidos por el programa.

Finalmente, se establecieron condicionales para la realización de las distintas rutinas del robot así como el manejo de las entradas y salidas digitales como se puede observar en el siguiente apartado.

## Diagrama de Flujo de acciones del robot

[INSERTAR EL DIAGRAMA DE FLUJO]

## Plano de planta de la ubicación de cada uno de los elementos

Para llevar a cabo la práctica, se posicionó el plano de trabajo a una distancia de X mm desde el suelo (eje z) y a una distancia de X mm desde el eje z del robot (eje x).

[INSERTAR IMAGENES DE LA UBICACION DE LOS ELEMENTOS]

## Descripción de las funciones empleadas

**FUNCIONES DEL PROGRAMA**

* **SetDO** : Esta función se utiliza para establecer el estado de una salida digital. Permite activar o desactivar una salida digital específica.
* **MoveL** : Esta función se utiliza para mover el robot en una trayectoria lineal definida en el espacio cartesiano. Esto significa que el robot se mueve de un punto a otro en línea recta en el espacio de trabajo, manteniendo la orientación de la herramienta.
* **MoveJ** : Esta función se utiliza para mover el robot en una trayectoria definida de manera interpolada en el espacio de las articulaciones. Es decir, el robot se mueve de un punto a otro a través de una serie de movimientos articulares continuos, donde la orientación de la herramienta puede variar.

  
**FUNCIONES CREADAS**

* **Dibujar**: Esta función se encarga de darle las instrucciones al robot para que realice las trayectorias necesarias para la realización del dibujo, su ejecución depende de la entrada digital DI_01 y durante su ejecución mantiene encendida la salida digital DO_01.
* **Home**:  Esta función se encarga de enviar al robot el HOME establecido por los miembros del grupo.
* **Mantenimiento**:  Esta función se encarga de darle las instrucciones al robot para que realice la trayectoria necesaria para poner el robot en posición de manteniemiento, su ejecución depende de la entrada digital DI_02 y durante su ejecución mantiene encendida la salida digital DO_02.

  
## Video Demostrativo
A continuación se añaden los vídeos de los resultados obtenidos del laboratorio, así como una foto del dibujo final:

[INSERTAR FOTO DEL DIBUJO FINAL]

Vídeo de la simulación en RobotStudio:

[NOMBRE](Link)

Vídeo de la demostración en vivo del funcioamiento:

[Nombre](Link)
