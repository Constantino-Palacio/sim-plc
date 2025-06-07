# Simulación con LogixPro
Trabajo realizado para la asignatura "Instrumentación y Control" (E0304) usando la herramienta LogixPro. Dado un determinado escenario de trabajo, se deben programar tres modos de operación.

<div align="center"><img src="https://github.com/user-attachments/assets/91ea0512-6c94-4b7a-9868-0a44c27ae868" style="width:50%;height:50%;text-align:center;"></img></div>

## Escenario de Trabajo
Este escenario simula una planta de procesamiento por lotes. El sistema consiste en un tanque donde se deben mezclar distintos líquidos siguiendo una secuencia determinada.

Se cuenta con dos válvulas de entrada y una tercera para vaciado. Hay sensores de nivel bajo y alto que indican la cantidad de líquido en el tanque. También se dispone de un agitador y un calefactor.

El operario puede controlar el sistema mediante pulsadores que activan el proceso, seleccionan modos de operación o inician etapas específicas. Al finalizar el lote, el contenido del tanque se descarga por completo y el sistema queda listo para comenzar un nuevo ciclo.

## Modo 1
Funciona como un ciclo automático de producción por lote. El operario solo necesita presionar un botón de inicio para que el sistema ejecute todo el proceso. El cual consta de: Apertura de la válvula hasta llenar el tanque, activación del agitador por 10 segundos, activación del calefactor por 15 segundos, apertura de la válvula de descarga hasta vaciado total del tanque.

## Modo 2
Este modo requiere intervención del operario. Se ejecuta por pasos, cada uno activado manualmente mediante el botón enter. Se llena el tanque con la primera válvula hasta el nivel medio, luego de la segunda válvula se completa hasta llenar el tanque. A continuación activa el agitador durante 10 segundos. cuando finalice se activa el calefactor durante 15 segundos. y con el botón de stop se vacía el tanque por completo.

## Modo 3
El usuario selecciona entre 3 tipos de productos con diferentes proporciones de agua y aditivos, además de tiempo de agitación o calentamiento.
- Producto A: 70% válvula 1 / 30% válvula 2 – 10s agitado – 10s calentado.
- Producto B: 50% válvula 1 / 50% válvula 2 – 15s agitado – 20s calentado.
- Producto C: 80% válvula 1 / 20% válvula 2 – 5s agitado – sin calefacción.

La selección se hace con pulsadores y el sistema ejecuta automáticamente la secuencia según el tipo elegido.
