---
tags:
  - proyecto-intermodular
  - DAM2
unidad: 1
tema: Nuevas ideas con valor de mercado
---

# Nuevas ideas con valor de mercado

## Criterios

Para que una idea "valga en el mercado" se ha buscado:

1. **Alguien que pague o que tenga el problema de verdad.** Las soluciones para negocios o centros (B2B) suelen tener más salida que las apps de consumo.
2. **Usuarios reales a mano** para probarla antes de la entrega.
3. **Un hueco** frente a lo que ya existe.
4. **Encaje con el equipo:** núcleo para el líder y módulos repartibles.

> Mismos supuestos que en `02-analisis-propuestas.md`: equipo de 4–5, horas de equipo ≈ 1,4× las de una persona sola.

## Resumen

| # | Idea | Horas equipo | Horas líder | Coste cognitivo | Reparto | Valor de mercado |
| - | ---- | ------------ | ----------- | --------------- | ------- | ---------------- |
| A | Diario de formación en empresa (FP Dual) | 260–340 h | 90–120 h | 3 | **Alto** | Alto (todos los centros de FP) |
| B | Del ticket a la despensa | 280–380 h | 110–150 h | 4 | **Alto** | Medio–alto |
| C | Gestión de clubes deportivos pequeños | 260–350 h | 90–120 h | 3 | **Alto** | Probado, pero saturado |

---

## A. Diario de formación en empresa (FP Dual)

**Contexto**
Con la Ley Orgánica 3/2022 de FP, toda la oferta es dual desde el curso 2024/2025: cada alumno pasa una parte de su formación en una empresa, con un tutor en el centro y otro en la empresa que comparten el seguimiento. Las plataformas oficiales de cada comunidad autónoma cubren sobre todo la parte administrativa (convenios, anexos, evaluación final).

**Definición**
App que conecta alumno, tutor de empresa y tutor del centro para el **seguimiento diario** de la formación en empresa, vinculando cada actividad a los resultados de aprendizaje (RA) del ciclo.

**Objetivos**
- MVP
  - **Alumno (app móvil):** diario de actividades y horas, vinculando cada actividad a sus RA.
  - **Tutor de empresa (web ligera):** valida el diario y valora en un par de clics, sin instalar nada.
  - **Tutor del centro (panel web):** estado de todos sus alumnos, RA cubiertos y pendientes, alertas si alguien se queda atrás.
- Ampliaciones
  - Exportación en el formato de los anexos de tu comunidad autónoma.
  - Mensajería entre los tres perfiles.
  - Recordatorios de visitas y reuniones de seguimiento.

**Estimación**
- Horas: 260–340 h de equipo, 90–120 h del líder.
- Coste cognitivo: **3**. Tres perfiles con permisos distintos y un modelo de datos bien pensado, pero sin tecnologías exóticas.

**Reparto en equipo: alto**
- Del líder: backend, autenticación, roles y permisos, modelo de RA.
- Delegable: **un perfil por persona** (app del alumno, web del tutor de empresa, panel del tutor del centro) + exportaciones.

**Qué destaca sobre el mercado**
- **Complementa, no compite** con las plataformas oficiales: cubre el día a día, que es donde está la carga de coordinación.
- **Usuarios reales en vuestro propio centro**: podéis enseñarla a vuestros tutores y validarla antes de entregar. Es el argumento más fuerte en la presentación.
- **Escala a cualquier centro de FP de España.**

**Riesgos**
- Cada comunidad tiene su plataforma y sus anexos: empezar por la vuestra.
- Datos personales de menores en algunos ciclos: cuidar permisos y RGPD.
- **A validar:** preguntad a vuestro tutor de prácticas cómo se hace hoy el seguimiento diario. Si ya tienen una herramienta que funciona, el hueco se estrecha.

---

## B. Del ticket a la despensa

**Definición**
Escaneas el ticket de la compra y la app hace tres cosas a la vez: registra el gasto, añade los productos a tu despensa con su fecha de caducidad estimada y te propone recetas con lo que está a punto de caducar.

Amplía el **Gestor de gastos (5)** y reutiliza el enfoque de IA del **proyecto 3**.

**Módulos**
| Módulo | Qué hace |
| ------ | -------- |
| Lectura de tickets | Foto del ticket → productos, cantidades y precios (OCR + IA) |
| Gastos | Lo que ya tenía el proyecto 5, pero con detalle por producto |
| Despensa | Inventario de casa con caducidades y avisos |
| Recetas | Sugerencias con IA según lo que hay y lo que caduca antes |

**Objetivos**
- MVP
  - Lectura de tickets de los supermercados más comunes.
  - Gastos por categoría y por producto.
  - Despensa con avisos de caducidad.
- Ampliaciones
  - Recetas con IA.
  - Evolución de precios de un mismo producto entre compras.
  - Despensa compartida entre convivientes.

**Estimación**
- Horas: 280–380 h de equipo, 110–150 h del líder.
- Coste cognitivo: **4**. Cada cadena imprime el ticket a su manera y las abreviaturas son difíciles de interpretar.

**Reparto en equipo: alto**
- Del líder: lectura de tickets e integración de IA.
- Delegable: un módulo por persona (gastos, despensa, recetas).

**Qué destaca sobre el mercado**
- Las apps de gastos saben **cuánto** gastas; esta sabe **en qué producto**, y por tanto ve subidas de precio y lo que tiras.
- Une tres apps que normalmente van separadas (gastos, despensa, recetas) con una sola acción: hacer una foto.
- Discurso fácil de vender: ahorro y menos desperdicio de comida.

**Riesgos**
- Precisión de la lectura: permitir corregir a mano siempre.
- Coste de la API de IA por ticket.

---

## C. Gestión de clubes deportivos pequeños

**Definición**
App para clubes y escuelas deportivas pequeñas: asistencia a entrenamientos, cuotas, convocatorias y avisos a familias.

**Valor de mercado: probado, pero saturado**
- Hay demanda real y empresas que viven de ello: **Clupik** (Madrid) supera los 1.000 clientes y factura en torno a 1,2 M€ al año; **SportEasy** tiene decenas de miles de equipos activos; también **SportMember**, **Esportter** o **Team App**.
- Muchos clubes siguen funcionando con WhatsApp y hojas de cálculo.

**Para que tenga sentido, hay que estrechar el foco**, por ejemplo:
- Solo **escuelas deportivas municipales**, con el ayuntamiento como cliente.
- Un único deporte, con sus necesidades concretas.
- Lo mínimo posible: asistencia con QR y cuotas, gratis para clubes muy pequeños.

**Estimación**
- Horas: 260–350 h de equipo, 90–120 h del líder.
- Coste cognitivo: **3**.

**Reparto en equipo: alto** (asistencia, cuotas, calendario, avisos como módulos).

---

## Descartadas tras investigar

| Idea | Por qué se descarta |
| ---- | ------------------- |
| Carta digital con alérgenos para restaurantes | Muy saturado y con opciones gratuitas (BuenaCarta) o integradas en el TPV (Qamarero, Foodtic) |
| App para comunidades de vecinos | Muchas alternativas que ya cubren reservas, votaciones e incidencias (ResidenciAPP, Onzane, TucomunidApp, Plusvecinos) |
| Control de stock para hostelería | Dominado por empresas especializadas con financiación (Gstock, Yurest) |

---

## Comparativa final (todas las ideas)

| Proyecto | Encaje con el equipo | Valor de mercado | Dificultad para el líder |
| -------- | -------------------- | ---------------- | ------------------------ |
| **A. Diario FP Dual** | Alto | Alto | Media |
| **3. Seguimiento con IA** | Alto | Medio | Media–alta |
| **B. Del ticket a la despensa** | Alto | Medio–alto | Alta |
| 4. Gamificador de hábitos | Alto | Medio–bajo | Media |
| C. Clubes deportivos | Alto | Probado, saturado | Media |
| 6. Material escolar | Medio–alto | Medio | Media–alta |
| 1. Apuntes | Medio | Bajo | Alta |
| 8 / 9. Hardware | Bajo | Bajo | Muy alta |

## Fuentes

- [Nueva FP dual desde el curso 2024/2025 (EPALE, Comisión Europea)](https://epale.ec.europa.eu/es/content/la-nueva-fp-en-extremadura)
- [Tutores del centro y de la empresa en la FP Dual (Parlamento de Navarra)](https://parlamentodenavarra.es/en/tramite-documento/1531140)
- [Gestión de la FP Dual en la Comunitat Valenciana (plataforma SAÓ)](https://ceice.gva.es/documents/388109149/399604262/_LOE-LOGSE_FPDUAL_Gesti%C3%B3n+de+la+FP+Dual.docx/37ac1bb8-3528-48d6-9d20-43fab52308a4)
- [Coordinación centro–empresa en la FP Dual (Revista Complutense de Educación)](https://revistas.ucm.es/index.php/RCED/es/article/view/70992)
- [Clupik (descubre.vc)](https://www.descubre.vc/e/clupik)
- [SportEasy en España (Merca2)](https://www.merca2.es/2022/09/23/sporteasy-aplicacion-deportiva-que-arrasa-espana-1084855/)
- [Esportter (El Referente)](https://elreferente.es/?p=18973)
- [BuenaCarta](https://buenacarta.com/en/)
- [Carta digital de Qamarero](https://www.qamarero.com/carta-digital/)
- [ResidenciAPP (App Store)](https://apps.apple.com/mx/app/residenciapp/id6744846844)
- [Gstock (Alimarket)](https://www.alimarket.es/restauracion/noticia_amp/335998/gstock-cierra-una-ronda-de-financiacion-por-600-000--)
