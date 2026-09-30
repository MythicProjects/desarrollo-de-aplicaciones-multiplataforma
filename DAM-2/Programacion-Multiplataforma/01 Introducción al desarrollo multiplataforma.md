# Unidad 1 - Introducción
## ¿Qué implica desarrollar para movil?  
**Desarrollo nativo**
Android -> Kotlin/Java
iOS -> swift
Máximo control de cada plataforma

**Desarrollo multiplataforma**
Una base de codigo compartiva.
React Native és una de las opciones
Tienen como objetivo Android e IOS

**React Native**
JavaScript
Componentes - Piezas pequeñas construidas
Comoposición - piezas que forman las interfaces
Reutilización - Objetivo, escribir una sola vez y reutilizarla

**React no es React Native**
React:
Components 
- Cada componente tiene su estado

Props
Estat
Hooks

React Dom
Interfaces web navegador
Inyectar información al Dom

React Native
Interficies mobiles Android + iOS
Composición de componentes reciclables entre web y movil

**Stack**
VS Code
Node.js - runtime
pnpm - paquetes
Vite - project React
React - Componentes
Expo - React Native

Instalación pnpm, node y react

## Instalar Node.js + pnpm y crear un proyecto con Vite (CachyOS)

https://vite.dev/guide/
https://react.dev/learn
 1. Instalar Node.js y pnpm
```bash
sudo pacman -S nodejs pnpm
```
Comprobar la instalación:
```bash
node -v
pnpm -v
```

2. Crear un proyecto con Vite
```bash
pnpm create vite
```

Crear en carpeta o dirección deseada

```bash
cd ~/ruta/que/quieras
pnpm create vite
```

O indica la ruta directamente al crearlo:

```bash
pnpm create vite ~/ruta/que/quieras/mi-proyecto
```

Opciones elegidas:
- **Project name:** testing-project
- **Framework:** React
- **Variant:** JavaScript
- **Linter:** ESLint
- **Install with pnpm and start now:** Yes

3. Arrancar el proyecto
El servidor arranca solo y se abre en: [http://localhost:5173/](http://localhost:5173/)
Para arrancarlo más adelante:

```bash
cd ~/testing-project
pnpm dev
```

Para pararlo: `Ctrl + C`

> **Nota:** pnpm se actualiza con `sudo pacman -Syu`, no con el `curl` que sugiere el aviso de actualización.


JS:
https://developer.mozilla.org/en-US/docs/Web/JavaScript
https://javascript.info/


Creación de componente
Estructura - Función con un return

Dudas resueltas:
- Se suele trabajar en carpetas "componente" y "páginas" (como vi en Angular)
- El main se suele dejar para pluguins o librerias que necesita, entre otros. 
- Se desarrolla toda la App sobre App.jsx


Creación de componentes

Componentes con paso de parámetros


Estamos viendo los estados
- Información que puede cambiar mientras la app se ejecuta
- Cada uno tiene su estado propio
- Evento: una acción que el usuario puede modificar el estado
- Render: React actualiza la interfaz

Ahora Listas y ejecutar listas
Datos - array de objetos
Recorrer un array -> usar map()

Modelo mental ReactNative:
```html
<div> -> <View>
<p> / <span> -> <Text>
<img> -> <image>
<button> -> <Pressable>
<css> -> <style>
```

React native - componentes i modelo react aplicado a interfaces nativas
Expo - Encargado de simplificar el proyecto, desarrollo y acceso a apis
Plataformas - Base de codigo con posibles adaptaciones

Entorno React Native:
VSCode
pnpm
expo
AndroidStudio
xCode
Dispositivo real o emulador

info: adb

Multiplataforma
Permisos - No siempre se delcaran o se piden igual
Hardware - No todos los dispositivos tienen las mismas capacidades
APIs - Tienen algunas funcionalidades específicas
UI / comportamiento - Diferentes comportamiento según el dispositivo



