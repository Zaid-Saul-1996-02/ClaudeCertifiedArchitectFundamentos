# Repaso — Preguntas más falladas por dominio.

Clase de refuerzo CCA · Dominios 1 y 2 (8 al 15 de junio 2026).

---

## Dominio 1 — Arquitectura y orquestación de agentes

### 1. E1.P39 — Rutas ligeras y enrutamiento dinámico · 5 fallos

**Enunciado:** Tu coordinador siempre invoca el pipeline completo de subagentes —búsqueda, análisis y síntesis— para cada solicitud. Durante la evaluación, descubres que incluso consultas simples (p. ej., recuperar un hecho conocido) activan todos los subagentes, lo que genera latencia y costo innecesarios. ¿Qué enfoque mejoraría la eficiencia del sistema de forma más eficaz? (Seleccione DOS)

**Respuesta(s) correcta(s):**
- Permitir que el coordinador omita subagentes innecesarios determinando cuáles se requieren para cada consulta
- Definir rutas de ejecución ligeras para consultas simples que eviten el pipeline completo

### 2. E3.P50 — Sesión nueva con resumen estructurado · 4 fallos

**Enunciado:** Estás usando Claude Code para analizar una base de código grande. Tras completar una sesión inicial, tu equipo modifica varios archivos. Reanudas la sesión previa usando --resume, pero el agente produce recomendaciones desactualizadas basadas en estados antiguos de los archivos. ¿Cuál es la forma más eficaz de manejar esta situación?

**Respuesta(s) correcta(s):**
- Iniciar una sesión nueva y proporcionar un resumen estructurado de los hallazgos previos junto con el contexto actualizado de los archivos

### 3. E2.P38 — Objetivos y criterios por encima de procedimientos rígidos · 4 fallos

**Enunciado:** Tu agente coordinador delega tareas en subagentes, pero observas resultados inconsistentes entre distintas consultas. En algunos casos, los subagentes siguen instrucciones rígidas y no logran adaptarse cuando se descubre nueva información durante la ejecución. Al revisar el prompt del coordinador, ves que proporciona instrucciones detalladas paso a paso sobre cómo deben realizar sus tareas los subagentes. ¿Cuál es la mejora más eficaz?

**Respuesta(s) correcta(s):**
- Reescribir el prompt del coordinador para que defina objetivos y criterios de calidad en lugar de instrucciones paso a paso

### 4. E3.P45 — Descomponer solicitudes con múltiples asuntos · 4 fallos

**Enunciado:** Un cliente reporta un problema complejo que involucra facturación, reembolso y cierre de cuenta. Tu agente intenta gestionar todo en una sola pasada, pero produce respuestas incompletas y poco claras. En algunos casos, el escalado a un agente humano carece de contexto suficiente, lo que obliga a una reinvestigación manual. ¿Qué cambios mejorarían de forma más eficaz tanto la calidad de la resolución como los traspasos de escalado? (Seleccione DOS)

**Respuesta(s) correcta(s):**
- Incluir un resumen de traspaso estructurado con detalles clave como el ID del cliente, el tipo de problema, la causa raíz y las acciones recomendadas
- Dividir la solicitud en asuntos distintos, investigar cada uno de forma independiente y luego combinar los resultados en una respuesta unificada

### 5. E2.P16 — Descomposición dinámica para auditorías abiertas · 3 fallos

**Enunciado:** Estás construyendo un agente para auditar una base de código grande en busca de vulnerabilidades de seguridad. El alcance inicial no está claro y los hallazgos tempranos suelen revelar nuevas áreas que requieren una investigación más profunda. La implementación actual usa una secuencia fija: escanear archivos → analizar resultados → generar informe. Sin embargo, en ocasiones se pasan por alto problemas importantes porque los nuevos hallazgos no se incorporan al flujo de trabajo. ¿Qué enfoque aborda mejor esta limitación?

**Respuesta(s) correcta(s):**
- Permitir que el agente genere dinámicamente tareas de seguimiento basadas en los hallazgos intermedios durante la ejecución

### 6. E2.P34 — Cadena más exploración adaptativa · 3 fallos

**Enunciado:** Estás diseñando un agente para revisar un pull request grande e identificar posibles problemas. El flujo de trabajo requiere un análisis consistente de cada archivo, pero también la capacidad de investigar patrones inesperados que surjan durante la revisión. Tu diseño actual usa un enfoque totalmente dinámico, pero los resultados son inconsistentes: algunos archivos se omiten y la cobertura varía entre ejecuciones. ¿Cuál es la mejora más apropiada?

**Respuesta(s) correcta(s):**
- Usar una secuencia estructurada para el análisis por archivo y luego permitir exploración adaptativa para hallazgos entre archivos o inesperados

### 7. E2.P40 — Pasar resultados completos de herramientas al contexto · 3 fallos

**Enunciado:** Tu agente recupera datos de un cliente y luego determina la siguiente acción según el resultado. Durante las pruebas, notas que el agente a veces toma decisiones de seguimiento incorrectas, aunque se llamó a la herramienta correcta y esta devolvió datos válidos. La investigación muestra que solo se pasa una versión resumida de la salida de la herramienta a la siguiente iteración, omitiendo campos clave necesarios para la toma de decisiones. ¿Cuál es la mejora más eficaz?

**Respuesta(s) correcta(s):**
- Pasar los resultados completos de las herramientas al contexto de la conversación para la siguiente iteración, en lugar de resúmenes parciales

### 8. E1.P26 — Aplicación selectiva de la verificación de identidad · 2 fallos

**Enunciado:** Tu agente gestiona actualizaciones de cuenta que pueden requerir o no verificación de identidad según el tipo de solicitud. Para mejorar la seguridad, un desarrollador añade un prerrequisito que fuerza la verificación de identidad antes de cualquier llamada a herramientas relacionadas con la cuenta. Tras el despliegue, observas mayor latencia y pasos de verificación innecesarios para operaciones de bajo riesgo (p. ej., actualizar preferencias de notificación), lo que afecta negativamente la experiencia de usuario. ¿Cuál es el ajuste más apropiado?

**Respuesta(s) correcta(s):**
- Aplicar la verificación de forma selectiva, de modo que la verificación de identidad solo se exija para operaciones de alto riesgo

### 9. E1.P47 — Descomposición híbrida para refactorización · 2 fallos

**Enunciado:** Estás construyendo un agente para refactorizar una base de código heredada. La tarea requiere primero entender la estructura del sistema, luego identificar áreas de alto impacto y, finalmente, aplicar mejoras dirigidas según las dependencias descubiertas. Un desarrollador implementa un enfoque híbrido: se usa un pipeline fijo para el mapeo inicial de la estructura, seguido de una secuencia rígida de pasos de refactorización aplicada a todos los componentes, sin importar los hallazgos. Durante las pruebas, el agente aplica cambios innecesarios en algunas áreas y omite mejoras críticas en otras. ¿Cuál es el ajuste más apropiado?

**Respuesta(s) correcta(s):**
- Usar descomposición dinámica tras el mapeo inicial de la estructura, de modo que los pasos de refactorización se adapten según las dependencias descubiertas

### 10. E1.P31 — Forzar pasos requeridos mediante prerrequisitos · 2 fallos

**Enunciado:** Tu agente procesa solicitudes de reembolso mediante un bucle agéntico. En algunos casos, el modelo inicia una secuencia de llamadas a herramientas, pero solo se completa parte del flujo requerido (p. ej., la verificación del cliente tiene éxito, pero se omite la búsqueda del pedido). El bucle termina con stop_reason = "end_turn" aunque no se completaron los pasos requeridos. Verificas que tu bucle comprueba correctamente stop_reason y sale cuando es "end_turn". ¿Qué cambio abordaría este problema de forma más eficaz?

**Respuesta(s) correcta(s):**
- Asegurar que los pasos requeridos del flujo se apliquen mediante prerrequisitos en lugar de depender únicamente de la decisión del modelo de continuar

### 11. E3.P13 — Anexar resultados de herramientas al contexto · 2 fallos

**Enunciado:** Tu agente recupera detalles de un pedido usando una herramienta y luego determina los próximos pasos según el resultado. Sin embargo, en producción, el agente llama repetidamente a la misma herramienta con entradas idénticas, sin avanzar hacia la resolución. La investigación muestra que los resultados de las herramientas no se incluyen en las solicitudes posteriores al modelo. ¿Qué cambio resolvería este problema de forma más eficaz?

**Respuesta(s) correcta(s):**
- Anexar los resultados de las herramientas al historial de la conversación antes de la siguiente iteración del bucle, para que el modelo pueda incorporar la nueva información a su razonamiento

### 12. E1.P4 — Completitud del contexto del subagente de síntesis · 2 fallos

**Enunciado:** Tu coordinador invoca un subagente de síntesis después de ejecutar los agentes de búsqueda y análisis. Sin embargo, solo se pasan adelante los hallazgos resumidos del agente de análisis, mientras que se omiten los resultados detallados de la búsqueda. En algunos casos, la salida de síntesis parece coherente pero pierde evidencia de respaldo clave y produce conclusiones incompletas. ¿Cuál es la solución más eficaz?

**Respuesta(s) correcta(s):**
- Incluir tanto los resultados de búsqueda en bruto como las salidas de análisis al invocar el subagente de síntesis

### 13. E3.P7 — Mapeo dinámico más estructural · 2 fallos

**Enunciado:** Estás construyendo un agente para añadir cobertura de pruebas completa a una base de código heredada grande. La estructura no está clara, las dependencias no están bien documentadas y el agente debe determinar dónde enfocarse primero. ¿Qué enfoques mejorarían de forma más eficaz la descomposición de tareas? (Seleccione DOS)

**Respuesta(s) correcta(s):**
- Permitir que el agente adapte dinámicamente su plan a medida que se descubren nuevas dependencias y patrones durante la ejecución
- Comenzar mapeando la estructura de la base de código e identificando áreas de alto impacto antes de generar un plan priorizado

### 14. E1.P20 — Reanudar y bifurcar para estrategias paralelas · 2 fallos

**Enunciado:** Estás analizando una base de código con Claude Code. Anteriormente completaste una investigación detallada de la arquitectura del sistema e identificaste varias áreas de mejora. Desde entonces: algunos archivos se han actualizado con cambios menores; quieres explorar en paralelo dos estrategias alternativas de refactorización; la mayor parte de tu análisis previo sigue siendo válido. ¿Qué acciones serían las más apropiadas para continuar este trabajo? (Seleccione DOS)

**Respuesta(s) correcta(s):**
- Usar --resume e informar al agente sobre los cambios específicos en los archivos antes de continuar
- Usar fork_session para crear ramas separadas para cada estrategia de refactorización

### 15. E1.P11 — Secuencia fija para verificaciones de cumplimiento · 2 fallos

**Enunciado:** Estás diseñando un agente para realizar verificaciones de cumplimiento en una base de código. El flujo de trabajo es consistente: validar convenciones de nombres, comprobar controles de acceso y verificar los requisitos de registro (logging) para cada archivo. Un desarrollador implementa un enfoque de descomposición totalmente dinámico en el que el agente decide qué verificaciones ejecutar según los hallazgos intermedios. Durante la evaluación, los resultados se vuelven inconsistentes: algunos archivos se omiten y, en ocasiones, se dejan fuera verificaciones obligatorias. ¿Qué cambio mejoraría la fiabilidad de forma más eficaz?

**Respuesta(s) correcta(s):**
- Usar una secuencia fija de verificaciones para cada archivo, de modo que todas las validaciones requeridas se apliquen de forma consistente

### 16. E1.P6 — Descomposición equilibrada de tareas · 2 fallos

**Enunciado:** Tu coordinador descompone consultas de investigación amplias en muchas subtareas de grano fino. Durante la evaluación, observas mayor latencia, hallazgos duplicados entre subagentes y una salida de síntesis fragmentada. Sin embargo, cuando reduces el número de subtareas, la cobertura se vuelve inconsistente. ¿Qué ajuste aborda mejor este compromiso?

**Respuesta(s) correcta(s):**
- Agrupar subtareas relacionadas en asignaciones menos numerosas y bien delimitadas que mantengan la cobertura sin fragmentación excesiva

### 17. E3.P35 — Prerrequisito que bloquea issue_credit · 2 fallos

**Enunciado:** Una auditoría de producción revela que, en aproximadamente el 9% de los casos, tu agente llama directamente a issue_credit usando la dirección de correo de un cliente sin confirmar primero la titularidad de la cuenta mediante verify_identity. Esto ha provocado que se apliquen créditos a las cuentas equivocadas cuando se proporcionan correos duplicados o desactualizados. ¿Qué cambio abordaría este problema de fiabilidad de forma más eficaz?

**Respuesta(s) correcta(s):**
- Añadir un prerrequisito programático que bloquee las llamadas a issue_credit y fetch_account hasta que verify_identity devuelva un ID de cuenta confirmado

### 18. E3.P26 — Paso de contexto estructurado entre agentes · 2 fallos

**Enunciado:** Estás construyendo un agente coordinador que delega en subagentes de búsqueda, análisis y síntesis. Durante las pruebas, observas que el agente de síntesis produce informes incompletos, omitiendo hallazgos clave que ya habían recuperado agentes anteriores. La investigación muestra que el coordinador invoca a los subagentes correctamente, pero solo pasa instrucciones mínimas sin incluir los resultados previos. ¿Qué cambios resolverían este problema de forma más eficaz? (Seleccione DOS)

**Respuesta(s) correcta(s):**
- Estructurar el contexto que se pasa entre agentes para separar el contenido de los metadatos, como fuentes y marcas de tiempo
- Incluir las salidas completas de los subagentes previos directamente en el prompt al invocar al siguiente subagente

---

## Dominio 2 — Diseño de herramientas e integración con MCP

### 1. E1.P18 — Herramienta Edit para modificaciones dirigidas · 5 fallos

**Enunciado:** Tu agente debe actualizar un valor de configuración que aparece en muchos archivos de un repositorio. El enfoque actual es: usar Read para cargar cada archivo, modificar el contenido en memoria y usar Write para sobrescribir el archivo. Durante las pruebas, esto funciona pero es lento y consume muchos recursos, especialmente en repositorios grandes. Quieres mejorar la eficiencia manteniendo la fiabilidad. ¿Cuál es la mejora más apropiada?

**Respuesta(s) correcta(s):**
- Usar la herramienta Edit cuando el cambio objetivo pueda identificarse de forma única dentro de cada archivo

### 2. E1.P15 — Restringir la herramienta general y reforzar la especializada · 4 fallos

**Enunciado:** Tu agente tiene dos herramientas: load_document: acepta URLs de documentos validadas y devuelve contenido estructurado; fetch_url: recupera contenido en bruto de cualquier URL. Ambas herramientas tienen descripciones claras. Sin embargo, ante URLs de documentos, el agente a veces usa fetch_url en lugar de load_document, lo que genera salidas inconsistentes. ¿Qué cambios mejorarían la selección de herramientas de forma más eficaz? (Seleccione DOS)

**Respuesta(s) correcta(s):**
- Restringir la herramienta más general acotando sus entradas aceptadas o aclarando su alcance
- Reforzar la descripción de la herramienta especializada para enfatizar sus casos de uso previstos

### 3. E2.P7 — Dividir una herramienta genérica en herramientas especializadas · 4 fallos

**Enunciado:** Tu sistema usa una sola herramienta: process_document: "Procesa documentos y devuelve información relevante". Durante las pruebas, notas salidas inconsistentes: a veces resume, a veces extrae datos y a veces intenta verificar. Los resultados varían significativamente según la formulación. ¿Cuál es la mejora más apropiada?

**Respuesta(s) correcta(s):**
- Dividir la herramienta en herramientas específicas con responsabilidades claramente definidas

### 4. E1.P44 — Aclarar el formato de salida en las descripciones · 3 fallos

**Enunciado:** Tus herramientas tienen descripciones, formatos de entrada y ejemplos claros. Sin embargo, durante las pruebas, el agente todavía selecciona de forma inconsistente entre dos herramientas: extract_entities: devuelve campos de datos estructurados; summarize_content: produce resúmenes narrativos. Ambas herramientas se usan correctamente de forma aislada, pero cuando las consultas implican tanto extracción como explicación, el agente tiende a favorecer el resumen incluso cuando se requiere una salida estructurada. ¿Qué cambio mejoraría mejor la fiabilidad de la selección de herramientas?

**Respuesta(s) correcta(s):**
- Aclarar las salidas de las herramientas enfatizando explícitamente resultados estructurados frente a no estructurados en sus descripciones

### 5. E1.P50 — Selección forzada de herramienta solo para el primer paso · 2 fallos

**Enunciado:** Tu flujo de trabajo requiere extraer metadatos primero, seguido de un enriquecimiento opcional según los resultados. Un desarrollador configura el agente con selección forzada de herramienta para llamar siempre a la herramienta de extracción de metadatos en cada turno. Durante las pruebas, observas que el agente llama repetidamente a la herramienta de extracción incluso cuando los metadatos ya se han recuperado, impidiendo avanzar a los pasos siguientes. ¿Qué cambio resolvería mejor este problema?

**Respuesta(s) correcta(s):**
- Usar la selección forzada de herramienta solo para el paso inicial y luego permitir la selección normal de herramientas en los turnos siguientes

### 6. E1.P10 — Descripciones de herramientas MCP para la selección · 2 fallos

**Enunciado:** Tu equipo integra un servidor MCP que ofrece capacidades avanzadas de búsqueda de código entre repositorios. Sin embargo, durante las pruebas, observas que el agente usa con frecuencia herramientas integradas como Grep en lugar de la herramienta MCP, incluso cuando esta proporciona resultados más precisos y completos. El servidor MCP está configurado correctamente y disponible para el agente. ¿Cuál es la mejora más apropiada?

**Respuesta(s) correcta(s):**
- Mejorar las descripciones de las herramientas MCP para explicar claramente sus capacidades, salidas y ventajas sobre las herramientas integradas

### 7. E3.P4 — Herramienta quick_lookup para mínimo privilegio · 2 fallos

**Enunciado:** Durante la evaluación, notas que tu agente de generación de informes se detiene con frecuencia para validar detalles básicos (p. ej., fechas, nombres, estadísticas simples). Actualmente delega estas comprobaciones de vuelta al coordinador, que invoca a un agente de recuperación y luego reanuda la generación del informe. Esto añade múltiples idas y vueltas y aumenta la latencia general en un 35%. El análisis muestra que aproximadamente el 80% de estas validaciones son búsquedas simples, mientras que el resto de los casos requieren una investigación más profunda en múltiples fuentes. ¿Cuál es el enfoque más eficaz para reducir la latencia manteniendo la fiabilidad del sistema?

**Respuesta(s) correcta(s):**
- Proporcionar al agente de generación de informes una herramienta quick_lookup limitada para validaciones simples, mientras que las comprobaciones complejas continúan a través del coordinador y el agente de recuperación

### 8. E2.P20 — Límites y contratos de E/S · 2 fallos

**Enunciado:** Tienes dos herramientas: extract_datapoints: extrae valores estructurados de documentos; summarize_content: produce resúmenes de alto nivel. Ambas herramientas tienen descripciones y ejemplos claros. Sin embargo, observas que el agente a veces usa summarize_content cuando la tarea requiere extraer campos específicos. ¿Qué cambios mejorarían la fiabilidad de la selección de herramientas de forma más eficaz? (Seleccione DOS)

**Respuesta(s) correcta(s):**
- Aclarar los límites de las herramientas indicando explícitamente qué no maneja cada una
- Incluir expectativas explícitas de entrada/salida en las descripciones de las herramientas
