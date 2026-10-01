---
tags:
  - programacion-de-servicios-y-procesos
  - DAM2
unidad: 1
tema: Introducción a servicios y procesos
---
# Introducción a servicios y procesos

Servicios y procesos


Info: 
- Arquitectura Risc
-  Arquitectura Cisc
- Microcódigo
- Pipeline
- Multithreading
- El procesador regula la ejecución de cada proceso
- Python - permite solo un núcleo por programa. No permite ejecución paralela. Protección llamada GIL (se está desbloqueando en las últimas versiones y al utilizar librerias creadas en C podría saltarse ese bloqueo)
- FAST API / TOMCAT
- Ejecución paralela
- Jerarquía chip-L1-L2-L3-memoria...
- Protección de hardware para que ejecutar procesos no salte en error
- Comunicar dos procesos es complejo y costoso -> aprovechar recursos, dentro del proceso se lanzan hilos
- Los hilos no estan dentro del proceso (capsula del proceso protegida) 
	- En la práctica: Si una variable hace falta estar en otro proceso, se usa un hilo y ya (no veo la diferencia entre proceso-proceso y a traves de hilo)
- Concepto DTO

Servicios:
- Concurrencia: No es una cola, se debe ofrecer servicio constantemente
- Se deben poder ejecutar cosas a la vez
- Es posible añadir más de una instrucción en el software
- Dividir instrucciones por núcleos
- La tecnología que nos permite aprovechar esto son los procesos en hilo
- Hay diferentes formas de realizar esto (ha mencionado 3)

Que cosas se ejecutan en paralelo: procesos, ejecutar por hilos y que no se bloqueen

Diferencia entre maximizar procesos e hilos

Mecanismos de sincronización en java mediante ejercicio de threats porque los hilos tienes problemas de sincronización
Objetivo: Creación de un servidor con múltiples peticiones



