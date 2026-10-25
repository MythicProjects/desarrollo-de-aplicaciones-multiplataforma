---
tags:
  - proyecto-intermodular
  - DAM2
unidad: 1
tema: Análisis de propuestas
---

# Análisis de propuestas

## Contexto del equipo

- Equipo de **4–5 estudiantes de DAM**.
- Solo una persona (líder técnico) puede hoy sacar adelante un proyecto de este tamaño.

Esto cambia cómo hay que valorar cada idea:

- **El líder es el cuello de botella.** Todo lo difícil (arquitectura, backend, integraciones) pasa por él, y además tiene que enseñar y revisar. Hay que contar con unas **5–8 h/semana del líder solo en revisar código, resolver dudas y desbloquear**.
- **Importa la divisibilidad.** Un buen proyecto para este equipo tiene un núcleo que monta el líder y muchas piezas acotadas que pueden hacer los demás: pantallas, CRUD, formularios, pruebas, datos de demo, documentación.
- **El hardware reparte mal.** Casi todo el trabajo físico y de firmware acaba en el líder.

### Reparto típico de roles

| Rol | Quién | Tareas |
| --- | ----- | ------ |
| Líder técnico | Tú | Arquitectura, base de datos, backend, integraciones difíciles, revisión de código |
| Desarrollo de módulos | 2–3 personas | Pantallas, CRUD, lógica de cada módulo sobre la base ya montada |
| Calidad y documentación | 1 persona (rotativo) | Pruebas, datos de demo, memoria, manual de usuario |
| Diseño | Compartido | Prototipos en Figma, guía de estilo |

### Supuestos de las estimaciones

- **Horas de equipo:** suma de todas las personas. Son ~1,4 veces las de una persona experta sola, por aprendizaje y coordinación.
- **Horas del líder:** la parte que no se puede delegar.
- Incluyen diseño, desarrollo y pruebas. **No** incluyen memoria ni presentación.

## Escala de coste cognitivo

| Nivel | Significado |
| ----- | ----------- |
| 1 | Todo conocido: CRUD, BD local, interfaz sencilla |
| 2 | Algo nuevo pero acotado (una API externa, gráficas, widgets) |
| 3 | Varias piezas nuevas que hay que integrar (backend + auth + app) |
| 4 | Problemas abiertos: sincronización, tiempo real, IA, marketplace |
| 5 | Mezcla software + hardware, depuración física, mucha incertidumbre |

## Resumen

| # | Proyecto | Horas equipo | Horas líder | Coste cognitivo | Reparto en equipo | Estado |
| - | -------- | ------------ | ----------- | --------------- | ----------------- | ------ |
| 1 | Software para apuntes | 250–350 h | 110–160 h | 4 | Medio | ✅ Definido |
| 2 | Detector de movimiento | — | — | — | — | 🔀 Fusionado en el 3 |
| 3 | Plataforma de seguimiento con IA | 300–420 h | 100–140 h | 4 | **Alto** | ✅ Definido |
| 4 | Gamificador de hábitos | 250–340 h | 80–110 h | 3–4 | **Alto** | ✅ Definido |
| 5 | Gestor de gastos | 130–200 h | 50–70 h | 2–3 | Alto, pero poco alcance | ✅ Definido |
| 6 | Material escolar de segunda mano | 230–310 h | 90–120 h | 4 | Medio–alto | ✅ Definido |
| 7 | App de estudio | 70–120 h | 20–30 h | 1–2 | Alto, pero muy pequeño | ✅ Definido |
| 8 | Consola emulador | 280–400 h | 180+ h | 5 | **Bajo** | ✅ Definido |
| 9 | SpaceMouse con botones | 250–350 h | 150+ h | 5 | **Bajo** | ✅ Definido |

---

## Centrado en software

### 1. Software para apuntes

**Definición**
Aplicación de toma de apuntes que reúne en un solo sitio notas, organización de archivos, tableros kanban, diagramas y calendario, priorizando lo práctico sobre la cantidad de funciones.

**Objetivos**
- MVP
  - Editor Markdown con carpetas y etiquetas.
  - Gestión de archivos adjuntos (PDF, imágenes) vinculados a notas.
  - Tablero kanban.
  - Calendario/agenda con eventos y fechas de entrega.
- Ampliaciones
  - Editor de diagramas sencillo.
  - Sincronización entre dispositivos.
  - Búsqueda de texto completo.
  - Módulo de tiempo de estudio (absorbe la idea 7).

**Estimación**
- Horas: 250–350 h de equipo, 110–160 h del líder.
- Coste cognitivo: **4**. El editor, el modelo de datos que une notas/tareas/eventos y la sincronización son lo difícil.

**Reparto en equipo: medio**
- Delegable: kanban, calendario, gestión de adjuntos, ajustes, temas.
- Del líder: editor, modelo de datos común, sincronización.

**Qué destaca sobre el mercado** (Obsidian, Notion)
- **Una sola fuente de verdad**: una tarea escrita en una nota aparece sola en el kanban y en el calendario, sin duplicar.
- **Archivos locales en Markdown**: sin dependencia de un servicio como Notion; los apuntes siguen siendo tuyos.
- **Listo para usar**: lo que Obsidian consigue con plugins, aquí viene integrado y configurado.
- **Pensado para estudiantes**: asignaturas, exámenes y entregas como conceptos propios.

**Riesgos**
- Es el proyecto con más tendencia a crecer sin control. Hay que congelar el alcance del MVP desde el principio.
- Mercado con gigantes muy consolidados: difícil de vender fuera del ámbito educativo.

---

### 2. Proyecto con detector de movimiento 🔀

Sin un propósito propio, no se sostiene como proyecto independiente. **Se propone integrarlo en el proyecto 3** como módulo de entrenamiento: la cámara del móvil detecta la postura, cuenta repeticiones y avisa de errores de técnica (p. ej. con ML Kit Pose Detection, que funciona en el propio dispositivo).

Así la idea de detectar movimiento tiene un uso claro y suma valor a otro proyecto en vez de competir con él.

---

### 3. Plataforma de seguimiento con IA

**Definición**
Plataforma modular en la que el usuario registra datos de distintos ámbitos y una IA los interpreta para devolverle información útil y personalizada, no solo gráficas. Cada ámbito es un módulo independiente sobre una base común.

**Módulos**
| Módulo | Qué registra | Qué aporta la IA |
| ------ | ------------ | ---------------- |
| Nutrición | Comidas (manual o por foto) | Estimación de calorías y macros, patrones de alimentación |
| Entrenamiento | Rutinas, series, pesos | Progresión, estancamientos, sugerencias de carga |
| Detección de movimiento *(antes idea 2)* | Vídeo de la cámara en tiempo real | Conteo de repeticiones y avisos de técnica |
| *Tercer módulo (abierto)* | Por decidir | Por decidir |

> **Propuesta para el tercer módulo:** *Descanso y recuperación* (sueño, cansancio percibido, agujetas). Es el que mejor cruza con los otros dos: permite a la IA explicar por qué un día se rinde menos.

**Objetivos**
- MVP
  - Base común: usuarios, perfil, almacenamiento de registros y servicio de IA compartido.
  - Módulos de nutrición y entrenamiento.
  - Resumen semanal generado por IA cruzando ambos módulos.
- Ampliaciones
  - Módulo de detección de movimiento.
  - Tercer módulo.
  - Registro de comidas por foto.

**Estimación**
- Horas: 300–420 h de equipo, 100–140 h del líder.
- Coste cognitivo: **4**. Integrar la API de IA, diseñar los prompts, validar respuestas y la detección de postura.

**Reparto en equipo: alto** — el mejor encaje para un equipo de 4–5
- Del líder: arquitectura modular, servicio de IA común, detección de movimiento.
- Delegable: **un módulo por persona o pareja**, con su propio CRUD, pantallas y gráficas. Cada uno tiene una parte clara que defender en la presentación.

**Qué destaca sobre el mercado** (MyFitnessPal, Strong, Hevy)
- **Interpretación en lugar de datos en bruto**: "esta semana has rendido menos los días que dormiste poco" frente a una gráfica que hay que leer.
- **Todo cruzado en una app**: nutrición, entrenamiento y descanso suelen estar en apps separadas que no se hablan.
- **Corrección de técnica con la cámara** sin hardware extra.

**Riesgos**
- Coste por uso de la API de IA: limitar llamadas y usar modelos pequeños o en el dispositivo cuando se pueda.
- Estimar calorías por foto es poco preciso; presentarlo como aproximación.
- Los datos de salud son categoría especial en el RGPD: guardarlos en local o cifrados.

---

### 4. Gamificador de hábitos

**Definición**
Aplicación en la que el usuario registra los hábitos que quiere adquirir o dejar. Cumplirlos mejora sus "estadísticas" de personaje, y puede compararse y retarse con otros usuarios.

**Objetivos**
- MVP
  - Alta de hábitos (adquirir o dejar) con frecuencia.
  - Registro diario y rachas.
  - Estadísticas ligadas a categorías: deporte → fuerza, lectura → intelecto, etc.
  - Perfil con nivel y progreso.
  - Red social básica: amigos y perfiles. *Con el equipo ya cabe en el MVP.*
- Ampliaciones
  - Retos de grupo.
  - Logros e insignias.

**Estimación**
- Horas: 250–340 h de equipo, 80–110 h del líder.
- Coste cognitivo: **3**, **4** con la red social (backend, autenticación, privacidad).

**Reparto en equipo: alto**
- Del líder: backend, autenticación, motor de estadísticas.
- Delegable: hábitos, perfil, pantallas sociales, logros, notificaciones.

**Qué destaca sobre el mercado** (Habitica, Finch, Streaks)
- **Estadísticas con significado**: cada hábito sube un atributo concreto, así el perfil refleja en qué estás trabajando de verdad.
- **Retos entre amigos** en lugar de un ranking global, que suele desmotivar.
- Más ligera que Habitica, cuya capa de rol puede abrumar.

**Riesgos**
- Hacer trampa es fácil en registro manual; aceptarlo o limitarlo por diseño.
- Monetizar apps de hábitos es difícil: valor de mercado moderado.

---

### 5. Gestor de gastos

**Definición**
App para anotar gastos manualmente, sin conexión con el banco, y ver en qué se va el dinero.

**Objetivos**
- MVP
  - Registro rápido de gastos con categoría.
  - Presupuestos mensuales por categoría.
  - Gráficas y resumen mensual.
  - Bloqueo con biometría o PIN.
- Ampliaciones
  - Gastos recurrentes.
  - Widget de registro en dos toques.
  - Exportación a CSV.

**Estimación**
- Horas: 130–200 h de equipo, 50–70 h del líder.
- Coste cognitivo: **2–3**.

**Reparto en equipo: alto, pero poco alcance**
- Se reparte bien, pero para 4–5 personas se queda corto. Ver la idea *Del ticket a la despensa* en `03-nuevas-ideas.md`, que lo amplía.

**Qué destaca sobre el mercado** (Spendee, Wallet, Money Manager)
- **Privacidad por diseño**: sin cuenta, datos solo en el dispositivo y base de datos cifrada (p. ej. SQLCipher).
- **Registro ultrarrápido**: el principal motivo de abandono del registro manual es la fricción.

**Riesgos**
- Mercado muy saturado; la diferencia está en privacidad y rapidez.

---

### 6. App de compraventa de material escolar

**Definición**
Marketplace exclusivo de material escolar, centrado en libros de texto de segunda mano, con verificación por código ISBN.

**Objetivos**
- MVP
  - Publicar anuncios escaneando el código de barras del libro.
  - Validación del ISBN y autocompletado de título, edición y portada (Google Books / Open Library).
  - Búsqueda y filtros.
  - Chat entre comprador y vendedor.
- Ampliaciones
  - Listas de libros por centro y curso: "necesito los libros de 2º ESO del IES X" y la app muestra qué hay disponible.
  - Valoraciones de usuarios.

**Estimación**
- Horas: 230–310 h de equipo, 90–120 h del líder.
- Coste cognitivo: **4**. Backend, autenticación, chat y moderación.

**Reparto en equipo: medio–alto**
- Del líder: backend, chat en tiempo real, autenticación.
- Delegable: escáner e integración ISBN, anuncios, búsqueda, listas por centro, valoraciones.

**Qué destaca sobre el mercado** (Wallapop, Vinted)
- **Edición correcta garantizada**: el ISBN evita comprar una edición que el centro ya no usa, el error más común.
- **Búsqueda por lista del centro** en lugar de libro a libro.
- **Entrega en mano por zona/centro**, sin pagos dentro de la app.

**Riesgos**
- Un marketplace sin usuarios no tiene valor: para la demo hay que cargar datos de prueba.
- Uso muy estacional (septiembre y junio).
- Evitar gestionar pagos reales.

---

### 7. App de estudio

**Definición**
Seguimiento minimalista del tiempo de estudio: cronómetro y acumulación de minutos por día.

**Objetivos**
- Cronómetro y registro manual.
- Minutos por día y por asignatura.
- Mapa de calor anual (estilo contribuciones de GitHub).
- Widget y objetivos diarios.

**Estimación**
- Horas: 70–120 h de equipo, 20–30 h del líder.
- Coste cognitivo: **1–2**.

**Qué destaca sobre el mercado** (Forest, Study Bunny)
- **Minimalismo real**: sin mascotas, tiendas ni monedas; solo tus minutos.

**Valoración**
- Demasiado pequeño para un equipo de 4–5. Encaja como **módulo** del proyecto 1 (apuntes) o del 4 (hábitos), y es una buena primera tarea para alguien que esté empezando.

---

## Implica hardware

### 8. Consola emulador

**Definición**
Consola portátil con sistema personalizado que integra distintos emuladores, con carcasa impresa en 3D y materiales de calidad.

**Objetivos**
- MVP
  - Hardware: placa (tipo Raspberry Pi), pantalla, mandos, batería.
  - Carcasa diseñada e impresa en 3D.
  - Lanzador propio que unifica los emuladores.
- Ampliaciones
  - Partidas guardadas en la nube.
  - Ajustes de energía y rendimiento por emulador.

**Estimación**
- Horas: 280–400 h de equipo, 180+ h del líder.
- Coste cognitivo: **5**.
- Coste económico en componentes.

**Reparto en equipo: bajo**
- El montaje, la electrónica y la integración con el sistema recaen en el líder.
- Delegable: el lanzador (interfaz) y el diseño de la carcasa.

**Qué destaca sobre el mercado** (Anbernic, Retroid, Miyoo, Batocera)
- Competir en precio con las consolas comerciales es inviable; la diferencia debe estar en el **lanzador propio** y en la **ergonomía**.

**Riesgos**
- En DAM se evalúa sobre todo el software: si el lanzador es poca cosa, el proyecto se queda cojo.
- Usar solo juegos homebrew o copias propias.

---

### 9. SpaceMouse con botones

**Definición**
Periférico de escritorio para controlar la vista en programas 3D (rotar, desplazar, hacer zoom con un solo mando) más una fila de botones programables, acompañado de una app de escritorio para configurarlo.

**Objetivos**
- MVP
  - Mando de 6 ejes: varios joysticks o sensores de efecto Hall con imanes bajo una tapa móvil.
  - Botones programables para atajos.
  - Microcontrolador con USB nativo (Arduino Pro Micro, ESP32-S3, RP2040) que el ordenador reconozca como dispositivo de entrada.
  - Carcasa impresa en 3D con peso para que no se mueva.
  - App de escritorio: calibración, sensibilidad y asignación de botones.
- Ampliaciones
  - **Perfiles por programa**: la app detecta si estás en Blender, Fusion o FreeCAD y cambia los atajos de los botones solo.
  - Conexión inalámbrica.
  - Compatibilidad con los drivers de 3Dconnexion (algunos proyectos caseros lo consiguen haciéndose pasar por un SpaceMouse; hay que investigarlo).

**Estimación**
- Horas: 250–350 h de equipo, 150+ h del líder.
- Coste cognitivo: **5**. Lectura y filtrado de sensores, matemáticas de 6 ejes, protocolo USB, calibración.

**Reparto en equipo: bajo**
- Firmware, electrónica y protocolo recaen en el líder.
- Delegable: **la app de escritorio** (perfiles, interfaz, detección del programa activo) y el diseño de la carcasa. Esta app es la parte que justifica el proyecto en DAM, y hay que darle peso.

**Qué destaca sobre el mercado** (3Dconnexion SpaceMouse, TourBox)
- **Mucho más barato** y con **diseño y código abiertos**.
- **Perfiles automáticos por programa** gestionados desde una app propia.

**Riesgos**
- Lograr un control fino y sin derivas es difícil.
- Si los programas no lo reconocen de forma nativa, hay que hacerse pasar por teclado/ratón, con peor experiencia.

---

## Valoración con el equipo actual

- **Mejor encaje para el equipo:** la **Plataforma de seguimiento con IA (3)**. Un módulo por persona, núcleo claro para el líder, vistosa en la presentación y con la detección de movimiento integrada.
- **Alternativa sólida:** **Gamificador de hábitos (4)**. Se reparte bien y su dificultad es más controlada.
- **Desaconsejados con este equipo:** los de hardware (**8** y **9**). Casi todo el trabajo recaería en el líder.
- **Como módulos, no como proyectos:** **App de estudio (7)** y **Gestor de gastos (5)**, este último ampliado en `03-nuevas-ideas.md`.
