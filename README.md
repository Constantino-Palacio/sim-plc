# Simulación con LogixPro
Trabajo realizado para la asignatura "Instrumentación y Control" (E0304) usando la herramienta LogixPro. Dado un determinado escenario de trabajo, se deben programar tres modos de operación.

<div align="center"><img src="https://github.com/user-attachments/assets/91ea0512-6c94-4b7a-9868-0a44c27ae868" style="width:50%;height:50%;text-align:center;"></img></div>

## Escenario de Trabajo
Este escenario simula una planta de procesamiento por lotes. El sistema consiste en un tanque donde se deben mezclar distintos líquidos siguiendo una secuencia determinada.

Se cuenta con dos válvulas de entrada y una tercera para vaciado. Hay sensores de nivel bajo y alto que indican la cantidad de líquido en el tanque. También se dispone de un agitador y un calefactor.

El operario puede controlar el sistema mediante pulsadores que activan el proceso, seleccionan modos de operación o inician etapas específicas. Al finalizar el lote, el contenido del tanque se descarga por completo y el sistema queda listo para comenzar un nuevo ciclo.

## Modo 1
Funciona como un ciclo automático de producción por lote. El operario solo necesita presionar un botón de inicio para que el sistema ejecute todo el proceso. El cual consta de: Apertura de la válvula hasta llenar el tanque, activación del agitador por 10 segundos, activación del calefactor por 15 segundos, apertura de la válvula de descarga hasta vaciado total del tanque.

<div align="center"><img src="https://github.com/user-attachments/assets/df8a8f6c-3226-4acc-acd4-11b8b9106849" style="width:50%;height:50%;text-align:center;"></img></div>

Siguiendo el diagrama anterior, la operación es de la siguiente manera: El operador acciona el botón `START`. Comienza el proceso de carga del tanque con el líquido 1. Al llenarse, se cierra la válvula correspondiente, se enciende el mezclador y se dispara un temporizador de 10 segundos. Al pasar este tiempo, se apaga el mezclador, se enciende el calentador y se dispara otro temporizador de 15 segundos. Pasados los 15 segundos, se apaga el calentador y se procede a vaciar el tanque para volver a iniciar el proceso.

La operación se puede frenar con el botón `STOP`. Se completa el ciclo actual y se detiene. Para volver a iniciar, se debe volver a accionar `START`. Para ejecutar esta simulación, cargar el archivo `g4_batch_b_modo_1.rsl` en el LogixPro.

## Modo 2
Este modo requiere intervención del operario. Se ejecuta por pasos, cada uno activado manualmente mediante el botón`ENTER`. Se llena el tanque con la primera válvula hasta el nivel medio, luego de la segunda válvula se completa hasta llenar el tanque. A continuación activa el agitador durante 10 segundos. cuando finalice se activa el calefactor durante 15 segundos. y con el botón de stop se vacía el tanque por completo.

## Modo 3
El usuario selecciona entre 3 tipos de productos con diferentes proporciones de agua y aditivos, además de tiempo de agitación o calentamiento.
- Producto A: 70% válvula 1 / 30% válvula 2 – 10s agitado – 10s calentado.
- Producto B: 50% válvula 1 / 50% válvula 2 – 15s agitado – 20s calentado.
- Producto C: 80% válvula 1 / 20% válvula 2 – 5s agitado – sin calefacción.

La selección se hace con pulsadores y el sistema ejecuta automáticamente la secuencia según el tipo elegido.

<div align="center"><img src="https://github.com/user-attachments/assets/58b09d7c-0bd0-4f6c-8ab7-453e79df491b" style="width:50%;height:50%;text-align:center;"></img></div>

La imagen anterior muestra el programa principal. Cada unos de los bloques de subrutina se corresponde con cada uno de los siguientes diagramas.

Preparación de producto A:
<div align="center"><img src="https://github.com/user-attachments/assets/119dbae7-5511-4ddd-a2af-75caa3cd22a9" style="width:50%;height:50%;text-align:center;"></img></div>

Preparación de producto B:
<div align="center"><img src="https://github.com/user-attachments/assets/966acb56-1b42-41cb-81fc-c210d56d9fb2" style="width:50%;height:50%;text-align:center;"></img></div>

Preparación de producto C: no requiere calentamiento.
<div align="center"><img src="https://github.com/user-attachments/assets/a436c9ae-33ee-4ca5-80b9-4740854890dc" style="width:50%;height:50%;text-align:center;"></img></div>

La lógica de preparación de cada producto es muy similar, a excepción de las proporciones de fluido y tiempos de mezcla y calentamiento. Las proporciones de líquido se calculan mediante el medidor de flujo correspondiente. Se asume un valor de 280 pulsos de este medidor para un tanque lleno, así que se calcula para cada caso:
- 80%: 224 pulsos
- 70%: 196 pulsos
- 50%: 140 pulsos
- 30%: 84 pulsos
- 20%: 56 pulsos

La ejecución es totalmente automática: una vez accionado `START`, se repite el ciclo seleccionado indefinidamente. Se puede, al igual que en el modo 1, detener el proceso al terminar el ciclo actual accionando la entrada `STOP`.
