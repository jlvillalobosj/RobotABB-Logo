# RobotABB-Logo

# Grupo 2

- Julian Leonardo Villalobos Jiménez - jlvillalovbosj@unal.edu.co
- Jhonathann Alexander Gómez Velásquez - jhagomezve@unal.edu.co

El presente repositorio tiene por objetivo dar a conocer el funcionamiento del brazo robótico industrial IRB-140 de la marca ABB, en donde por medio de funciones y comandos que nos permitiran otorgarle movimientos deseados y precisos al robot se haga un esquema con las iniciales de nuestros nombres y el logo de una empresa conocida.

<p align="center">
  <img src="/Imágenes/BrazoRobotico.PNG" width="400" />
 <img src="/Imágenes/BrazoRoboticoUNAL.PNG" style="float:left;" />
</p>

## [Solucion planteada](RobotAbb-Logo)

## Diagrama de flujo

El diagrama de flujo presentado se basa en las acciones seriales del brazo robótico con las respectivas restricciones o condiciones que se consideran necesarias para el propósito del robot

<p align="center">
  <img src="/Imágenes/Diagrama BrzoRobotico.drawio.png" width="400" />
</p>

## Plano de planta

## Funciones utilizadas

## Herramienta

La herramienta se diseñó siguiendo las especificaciones del fabricante del robot para la base. Se le asignó un ángulo de inclinación de 45 grados para reducir la probabilidad de que se generaran singularidades en las trayectorias del robot. Su longitud se determinó para sujetar a presión el marcador utilizado. Asimismo, se dejó espacio en la base del marcador para la ubicación de un resorte que protege la herramienta y optimiza el resultado al momento de realizar la escritura. Por último se realizó la manufactura aditiva de la pieza considerando las tolerancias dimensionales de este tipo de manufactura.

<p align="center">
  <img src="/Imágenes/Tool1.PNG" width="400" />
</p>

<p align="center">

  <img src="/Imágenes/Herramienta.PNG" width="400" />
</p>

## [Código en RAPID](/LogoTesla/ControllerData/IRB140_6_81/RAPID/TASK1/PROGMOD/Module1.mod)

Para el diseño del código se inició crando una herramienta la cual me ayudaba como referencia para modificar el TCP en donde se establece como punto de referencia la punta del marcador ubicado sobre esta misma, esta se ajustó de modo que el eje Z se muestre en paralelo a la dirección del largo de la herramienta con el fin de asegurar que al ubicar de forma perpendicular el eje Z al plano, del mismo modo el marcador se iba a comportar

<p align="center">
  <img src="/Imágenes/CreacionHerramienta.PNG" />
 <img src="/Imágenes/TCP.PNG" style="width: 45%; height: auto;" />
</p>

Se procedio a establecer los diferentes *Targets* por donde se espera pasar el marcador, entre estos inicialmente se ubicaron el punto de mantenimiento *Target_Operator* en donde se hace el ajuste de la herramienta, la posicion de origen o inicial *Posicion_Inicial* en donde se ubica la esquina superior derecha de la hoja como su work object y finalmente el punto home del proyecto  *HOME*, en el cual se posiciona el robot cada que va a hacer un cambio de esquema y en donde va a terminar cuando culmine el programa. 
Por otro lado se diseñaron los *Targets* para los puntos sobre la superfuicie en cada una de las letras y del logo, estas se representaron como *Target(Letra que se va a dibujar)_(Numero de punto en la letra)*.

<p align="center">
  <img src="/Imágenes/EncabezadoCódigo.PNG" />
</p>

A continuación se diseñaron diferentes funciones para el path de cada una de las letras y del logo de tesla con el fin de facilitar detectar errores en el recorrido del código y especificar condiciones detalladas en cada una de las letras y símbolos, tales como velocidad de recorridos en paths específicos, niveles de precisión en algunos targets y tiempos de espera, es importante aclarar que al final de cada función el marcador pasa nuevamente por el target inicial de la letra para finalmente ir al *HOME* del proyecto.

<p align="center">
  <img src="/Imágenes/Paths.PNG" />
</p>

Finalmente para el diseño de la función principal *main()* se inició apagando todas las salidas del sistema con el objetico que el dispositivo se encontrara en un estado conocido cuando se empezara a manipular, se procedio a pausar el código hasta presentar una señal de entrada para iniciar el recorrido al estado de mantenimiento y a activar la salida del led1. Una vez hecho el ajuste de mantenimiento el codigo se pausa nuevamente hasta presentar otra señal de entrada la cual le permite llegar a la posición origen de la hoja apagando el led1 y dadole salida al led 2, finalmente al ingresar una tercera señal de entrada el sistema apaga el led 2 y activa el led 3 el cual nos indica que se esta realiazndo el dibujo, en este caso se pasa por cada una de las funciones (letras) para finalmente ubicar el marcador en la posición *HOME* del proyecto.

<p align="center">
  <img src="/Imágenes/Main.PNG" />
</p>

Para acceder al código puede seleccionar el subtítuo de esta sección "Código RAPID" o darle clic [aquí](/LogoTesla/ControllerData/IRB140_6_81/RAPID/TASK1/PROGMOD/Module1.mod)

## Videos de pruebas de funcionamiento
Simulación
https://github.com/jlvillalobosj/RobotABB-Logo/assets/57506705/320bad9b-4126-4240-a565-06e80536f104

Prueba Real
https://github.com/jlvillalobosj/RobotABB-Logo/assets/57506705/acefa244-26ae-4086-ad4b-36ae096dd5aa

