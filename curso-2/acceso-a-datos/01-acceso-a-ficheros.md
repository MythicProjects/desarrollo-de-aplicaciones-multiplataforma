---
tags:
  - acceso-a-datos
  - DAM2
unidad: 1
tema: Acceso a ficheros
---
# Unidad 1: Acceso a ficheros

Persistencia de datos

Tipos de ficheros de texto - Se pueden leer con un editor de texto
- txt -> texto plano
- xml -> fichero xml
- json -> ficher de intercambio d información
- props -> fichero de propiedades
- conf -> fichero de configuracion
- sql -> script SQL
- srt -> fichero de subtitulo

Ejemplos:

Tipos de ficheros binarios - Como ser humano no se pueden leer
- pdf
- jpg
- doc
- avi
- ppt
- bin
- dat

Uso de ficheros en la actualidad
XML eXtensible Markup Language
- Elementos con etiqueta
- Estructura jerárquica
- Las elementos pueden tener otros elementos

Trabajar con ficheros
- Se gestionan entradas y salidas (E/S) (I / O)
- Usan la API de java por defecto java.io
- Existen clases:
	- Para leer entrada 
	- Escribir entradas
	- Operar con ficheros en el sistema local
	- Serialización de objetos - Convertir objeto java en una secuencia de bytes

java.io - Class File
- Representación abstracta de ficheros y directorios
- Independientemente de la plataforma
	- Excepciones (IOException) - El fichero puede no estar, es imprescindible para evitar errores
- Posiblididades:
	- Renombrar
	- Borrar
	- Crear
	- Establecer fecha de modificación
	- Crear
	- Listar el contenido
	- Listar los nombres de archivo de la raíz

Diferencia entre PrintWriter y File
- File: Representa la ruta de un dichero y directorio; no escribe contenido
- PrintWriter: Permite escribir en un fichero

Clase Scanner

Escribir con FileWriter
BufferedWriter y Reader
- BufferedWriter - Mejora el rendimiento de escritura en disco o red
- BufferedReader- Optimiza la lectura
