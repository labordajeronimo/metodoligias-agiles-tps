# Resolución Ejercicios 18 y 19: Simulación de Scrum con IA

**Alumno:** Jerónimo Laborda
**Materia:** Metodologías Ágiles (2026)

---

## Ejercicio 18: Cadena de Prompts para Proyecto de Logística (Optimización de Última Milla)

A continuación, se detalla la secuencia lógica en cascada (*Prompt Chaining*) diseñada para simular un ciclo completo de Scrum. Cada etapa utiliza la estructura: Contexto + Instrucción + Input + Output.

### Prompt 1: Creando el Product Backlog (El "Qué")
* **Actividad Scrum:** Inicialización del proyecto y definición de necesidades por el Product Owner.
* **Técnica utilizada:** Clasificación de requerimientos e Historias de Usuario bajo criterios INVEST.
* **Estructura del Prompt:**
  > **Contexto:** Actúa como un Product Owner experto en la industria de logística de distribución urbana de última milla.
  > **Instrucción:** Transforma las necesidades del negocio en un Product Backlog inicial. Generá las 5 Historias de Usuario más importantes, priorizadas y con sus respectivos Criterios de Aceptación. El foco principal debe estar en la asignación inteligente de pedidos a los repartidores según su zona geográfica activa.
  > **Input:** Requerimientos iniciales de optimización de rutas, geolocalización de transportistas y balanceo de carga de entregas.
* **Output obtenido (Simulado):**
  1. *Como* despachador, *quiero* que el sistema asigne pedidos automáticamente por zona, *para* reducir el tiempo de planificación de rutas.
     * *Criterio de aceptación:* El algoritmo debe agrupar paquetes en un radio máximo de 3 km por repartidor.
  2. *Como* repartidor, *quiero* visualizar la ruta optimizada en mi app, *para* evitar congestiones de tráfico y entregar más rápido.
  3. *Como* cliente final, *quiero* recibir alertas SMS con el horario estimado de llegada (ETA), *para* estar presente al momento de la entrega.

---

### Prompt 2: Planificando el Sprint (El "Cómo" y el "Cuándo")
* **Actividad Scrum:** Sprint Planning (Definición del Sprint Backlog por los Developers).
* **Técnica utilizada:** Estimación relativa (Story Points), Descomposición de tareas y definición del Sprint Goal.
* **Estructura del Prompt:**
  > **Contexto:** Actúa como el equipo de desarrollo (Developers) autogestionado y el Scrum Master.
  > **Instrucción:** Tomando como base el Product Backlog anterior, simula nuestra planificación para un Sprint de 2 semanas. Elegí las 3 historias de mayor prioridad que el equipo sea capaz de comprometerse a completar. Estimá cada una en Puntos de Historia usando la escala Fibonacci (ej. 3, 5, 8). Tomá la historia principal de asignación por zona y desglosala en tareas técnicas concretas. Como Scrum Master, definí un Sprint Goal claro y motivador.
  > **Input:** (Salida del Prompt 1)
* **Output obtenido (Simulado):**
  * **Sprint Goal:** "Lograr la asignación automática y el trazado de rutas base para el núcleo de repartidores de la zona centro."
  * **Historias Seleccionadas:** 
    * HU1: Asignación automática por zona (8 SP)
    * HU2: Visualización de ruta optimizada en mapa (5 SP)
  * **Desglose de Tareas (HU1):**
    * Tarea 1: Diseñar el modelo de datos para zonas y cuadrantes (Desarrollador Backend).
    * Tarea 2: Implementar el algoritmo de agrupamiento geográfico por código postal (Desarrollador Backend).
    * Tarea 3: Crear la interfaz de confirmación de asignación en el panel web (Desarrollador Frontend).

---

### Prompt 3: La Reunión Diaria (El "Día a Día")
* **Actividad Scrum:** Daily Scrum (Inspección y Adaptación diaria del plan).
* **Técnica utilizada:** Timeboxing (15 minutos), Sincronización de equipo y Gestión de Impedimentos.
* **Estructura del Prompt:**
  > **Contexto:** Actúa como el Equipo de Desarrollo y el Scrum Master en una sesión de sincronización.
  > **Instrucción:** Simula nuestra Daily Scrum en el día 5 del Sprint. Redactá la actualización de 3 desarrolladores con perfiles distintos (Frontend, Backend y QA) respondiendo al foco del Sprint Goal. El desarrollador Backend debe reportar un bloqueo crítico con la API de mapas. Mostrá la intervención del Scrum Master aplicando liderazgo servicial para registrar y destrabar el impedimento.
  > **Input:** (Sprint Backlog y Sprint Goal del Prompt 2)
* **Output obtenido (Simulado):**
  * **Dev Frontend:** "Ayer terminé la interfaz base del panel de asignación. Hoy voy a conectarla con los endpoints de prueba. No tengo bloqueos."
  * **Dev Backend (BLOQUEADO):** "Ayer intenté procesar las coordenadas del cuadrante centro, pero la API de mapas nos está rechazando las peticiones por un problema de límite de créditos en la cuenta de desarrollo. Hoy no puedo avanzar en el algoritmo de rutas hasta que se destrabe."
  * **Dev QA:** "Ayer preparé los entornos de prueba. Hoy iba a testear el algoritmo, pero me sumo a ayudar a Backend a revisar alternativas locales de mockeo."
  * **Intervención del Scrum Master:** "Tomo el impedimento de la API. Ya lo registro en nuestro tablero de bloqueos. Voy a comunicarme inmediatamente con el área de infraestructura y el Product Owner para gestionar la actualización de la licencia hoy mismo de forma urgente para que el equipo no pierda el foco."

---

### Prompt 4: Mostrando el Resultado (La "Review")
* **Actividad Scrum:** Sprint Review (Inspección del Incremento y Adaptación del Backlog).
* **Técnica utilizada:** Demostración de producto de valor (*Right Product*) y recolección de Feedback del cliente.
* **Estructura del Prompt:**
  > **Contexto:** Actúa como el Scrum Team y los Clientes/Stakeholders de la empresa de logística.
  > **Instrucción:** El Sprint terminó. Simula la Sprint Review. Actúa como el equipo y describe qué funcionalidades terminadas que cumplen la Definition of Done (DoD) le estamos mostrando al cliente en la demo. Luego, redacta el feedback que nos da el cliente evaluando la interfaz de asignación. Menciona cómo ese feedback genera de forma empírica una nueva historia de usuario (PBI) para el Product Backlog.
  > **Input:** (Incremento resultante del Prompt 3)
* **Output obtenido (Simulado):**
  * **Demo del equipo:** Se presenta el algoritmo de asignación automatizada corriendo en vivo y el panel web donde el despachador ve los paquetes agrupados correctamente por zona de reparto.
  * **Feedback del Cliente:** "La agrupación por zonas funciona excelente, pero en la práctica urbana el tráfico en hora pico rompe los perímetros fijos. Necesitamos que el sistema pueda recalcular las rutas considerando el tráfico en tiempo real."
  * **Impacto en el Backlog:** El PO valida el comentario y da de alta un nuevo Item (PBI) prioritario: *"Como despachador, quiero recalcular las rutas de reparto según el tráfico en vivo para mitigar demoras en las entregas."*

---

### Prompt 5: Aprendiendo para Mejorar (La "Retrospectiva")
* **Actividad Scrum:** Sprint Retrospective (Inspección del proceso, herramientas y relaciones).
* **Técnica utilizada:** Kaizen (Mejora continua) y definición de Planes de Acción medibles.
* **Estructura del Prompt:**
  > **Contexto:** Actúa como el Scrum Team en su espacio de introspección al cierre del ciclo.
  > **Instrucción:** Simula la Sprint Retrospective. El equipo debe identificar de forma clara: 1) Algo que funcionó muy bien y debemos mantener. 2) Un problema técnico u operativo que tuvimos durante las dos semanas. 3) Una acción de mejora concreta y medible (Action Item) para aplicar directamente en el próximo Sprint Backlog.
  > **Input:** (Lecciones y eventos ocurridos durante el desarrollo y la Review)
* **Output obtenido (Simulado):**
  1. **Lo que funcionó bien:** La comunicación diaria y la rapidez del Scrum Master para resolver el bloqueo de la API de mapas evitaron que el Sprint fracasara.
  2. **Problema detectado:** Depender de servicios externos sin un entorno de "Mock" o contingencia local nos dejó paralizados un día entero.
  3. **Action Item (Mejora medible):** *"Para el próximo Sprint, los Developers dedicarán las primeras 4 horas del desarrollo a crear respuestas simuladas (mocks) para cualquier API de terceros antes de codificar la lógica de producción, asegurando un desarrollo desacoplado."*

---

## Ejercicio 19: Configuración de Bots en Poe.com

Para dar soporte operativo al proceso Scrum, se estructuraron las siguientes directrices de comportamiento (*System Prompts*) para los bots en la plataforma Poe:

* **Bot Cliente:**
  * *System Prompt:* "Actúa como el cliente corporativo de logística. Tu función es formular requerimientos de negocio de distribución urbana al Product Owner, simular la ejecución de pruebas de aceptación de usuario y calificar los incrementos entregados en base al valor real que aportan a la operación."
* **Bot Scrum Master:**
  * *System Prompt:* "Actúa como un Scrum Master con enfoque de líder servidor. Tu tarea principal es coordinar la simulación de las reuniones diarias (Daily) recordando estrictamente la regla de límite de tiempo de 15 minutos y llevar un registro riguroso de impedimentos para asegurar el foco del equipo."
* **Bot Product Owner:**
  * *System Prompt:* "Actúa como Product Owner. Tu responsabilidad es administrar, priorizar y refinar los ítems del Product Backlog basándote en el retorno de valor y el contexto del negocio logístico. Recordale periódicamente al equipo las fechas límite y los objetivos de la Planning."
* **Bot Desarrollador:**
  * *System Prompt:* "Actúa como un Developer enfocado en calidad técnica y autogestión. Realizá el seguimiento de tus tareas asignadas en el Sprint Backlog, generá los reportes de avance simulados y levantá alertas tempranas ante la aparición de deuda técnica o errores."

---

## Análisis y Reflexión Metodológica

1. **Estrategia de Contextualización:** La clave del éxito de esta cascada radica en el *Prompt Chaining*. Al obligar a la IA a asumir un rol específico (sombrero técnico o de negocio) en cada paso, el modelo restringe su vocabulario al estándar de la disciplina, evitando respuestas genéricas.
2. **Resultados de Poca Calidad y su Motivo:** Al no especificar limitantes de negocio o técnicos en las primeras pruebas, la IA tendía a desglosar tareas infinitas o demasiado abstractas. Esto ocurre porque los LLMs carecen de contexto de capacidad real si el usuario no define parámetros de contención claros como el *timebox* o la *Definition of Done (DoD)*.
3. **Propuesta de Agente Unificado:** Para ejecutar este flujo en una sola acción de forma automática, se requeriría un orquestador basado en un framework de agentes distribuidos (como CrewAI o LangChain). Un "Agente Raíz" recibiría el requerimiento inicial del cliente y coordinaría de manera secuencial y autónoma la comunicación entre los sub-agentes (PO, SM y Devs), pasándoles los inputs y outputs de forma limpia a través de variables de entorno hasta consolidar el entregable final.
