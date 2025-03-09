PRACTICA 1
Este código básico utiliza la librería Arduino.h para interactuar con una placa Arduino. Enciende y apaga un LED conectado al pin digital 23 de la placa en un ciclo continuo utilizando la función loop(). El tiempo de encendido y apagado del LED es de un segundo cada uno, controlado por la función delay().

Dificultades del código:
No utiliza un control de errores: Si hay algún problema con el hardware o el código.
Uso de la función delay(): Esta función detiene todo el programa durante el tiempo especificado, lo que puede suponer problemas en programas más complejos.
Tiempo de funcionamiento:
El ciclo de encendido y apagado del LED dura aproximadamente 2 segundos, ya que cada estado (encendido y apagado) tiene un retraso de 1000 milisegundos (1 segundo). Este ciclo se repite continuamente, por lo que el tiempo de funcionamiento es indefinido mientras la placa Arduino esté alimentada.


graph TD; A[Inicio] --> B[Inicializar pin del LED]; B --> C[Encender LED]; C --> D[Esperar 1 segundo]; D --> E[Apagar LED]; E --> C;
