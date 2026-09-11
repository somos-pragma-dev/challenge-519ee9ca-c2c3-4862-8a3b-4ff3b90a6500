# Prompt para Mejorar el Codigo Base

Copia y pega el contenido del bloque de abajo en un asistente de IA (Claude, ChatGPT)
para obtener un ZIP con el proyecto completo y arrancable.

Si preferis trabajar en tu editor con un agente local (Claude Code, Cursor, Copilot), usa `AGENTS.md` en vez de este archivo: dice lo mismo pero para que escriba los archivos en disco.

## Las dos reglas que no se negocian

1. **Completa el boilerplate.** Todo lo que el proyecto necesita para compilar y arrancar: manifiesto de dependencias, punto de entrada, configuracion, capa de interfaz, y las capas del patron arquitectonico declarado. Eso es andamiaje y es tu trabajo.
2. **NO resuelvas el reto.** Los entregables de las fases son el trabajo de la persona. El hueco pedagogico se deja como esta: el proyecto arranca, pero lo que el reto pide implementar NO esta implementado.

Dicho de otra forma: si algo impide compilar, arreglalo. Si algo es logica de negocio incompleta, validaciones ausentes, un secreto hardcodeado o un patron mejorable, dejalo exactamente como esta — es lo que la persona tiene que encontrar.

## Como saber que terminaste

```bash
python3 -c "import csv,glob; [list(csv.DictReader(open(f))) for f in glob.glob('*.csv')]"
```

Ese comando corriendo sin errores es la definicion de "listo".

---

```
## Briefing del reto (autoridad)
Este bloque manda sobre los archivos adjuntos. El stack y el rol salen de AQUÍ, no de un topic genérico ni de markdown placeholder.

### Perfil
Chapter Business Consulting, Especialidad Business Consultant, Tecnología Metricas de Negocio, Advanced

### Brecha de conocimiento
Descompone la metrica objetivo en palancas accionables y prioriza por impacto y esfuerzo con supuestos explicitos

### Misión / candidato
Aumentar la activacion de clientes nuevos

### Reto
- Tema: Árbol de métricas y priorización de iniciativas
- Seniority: advanced-l2
- Tipo: practical
- Título: Diseño y priorización de iniciativas para aumentar la activación de clientes nuevos
- Tiempo estimado: 8 horas

### Fases (trabajo del HUMANO — PROHIBIDO completarlas)
No implementes estos entregables. Dejalos como hueco pedagógico. El asistente solo materializa el proyecto arrancable para que el participante pueda trabajar.
- Fase 1: Definición del árbol de métricas — objetivo: Crear un árbol de métricas que descomponga la activación de clientes nuevos en palancas accionables. — entregable (NO resolver): Árbol de métricas documentado.
- Fase 2: Priorización de iniciativas — objetivo: Priorizar las iniciativas identificadas en el árbol de métricas basándose en su impacto y esfuerzo. — entregable (NO resolver): Matriz de priorización de iniciativas.
- Fase 3: Revisión y ajustes — objetivo: Revisar y ajustar el árbol de métricas y la priorización de iniciativas basándote en feedback y nuevos datos. — entregable (NO resolver): Árbol de métricas y matriz de priorización ajustados.

Eres un asistente experto en análisis, corrección y generación de archivos de cualquier tipo:
código fuente, documentación, hojas de cálculo, documentos Word, configuraciones, entre otros.
Voy a enviarte una cadena de texto que contiene uno o más archivos. Cada archivo está delimitado por un marcador con el siguiente formato:
// === ARCHIVO: ruta/del/archivo.extension ===
o también puede aparecer como:
## === ARCHIVO: ruta/del/archivo.extension ===
Lo que sigue al marcador puede ser:

El contenido real del archivo (código, texto, YAML, etc.)
Una descripción en lenguaje natural de lo que debe contener el archivo


TU TAREA
PASO 0 — ¿Esto es un proyecto o una carcasa?
Antes de extraer archivos, leé el Briefing (si está) y diagnosticá el adjunto.

Es CARCASA si ocurre CUALQUIERA de estas:
- No hay manifiesto de dependencias del stack del briefing (manifest.json de VTEX IO / package.json / pom.xml / build.gradle / requirements.txt / go.mod / *.tf / *.csproj, según corresponda)
- Hay un "binario" que en realidad es un comentario ("no puede ser mostrado como texto plano", placeholder .fig/.docx vacío)
- Los markdowns ya completan entregables de fases posteriores ("se implementó fade-in", lista de áreas ya resuelta)

Si es CARCASA:
- MATERIALIZÁ un proyecto que arranca en el stack del briefing (VTEX IO Store Framework, Angular, Terraform, pytest, Nest, etc.). Incluí manifiesto, punto de entrada y capa de interfaz reales.
- NO copies los markdowns de "solución" como si fueran el producto. Son ruido de generación.
- NO resuelvas las fases del briefing (están marcadas PROHIBIDO). Dejá el hueco pedagógico: el flujo existe, las microinteracciones/calidad/infra que el reto pide NO están hechas.
- Después seguí al PASO 5 (ZIP).

Si es un proyecto REAL (manifiesto + código que compila o arranca):
- Seguí PASO 1 en adelante. 🔴 compilación sí. 🟡 pedagógico no.

PASO 1 — Detección y extracción
Identifica todos los archivos presentes en la cadena. Para cada archivo extrae:

Su ruta completa (ej: src/main/java/com/pragma/Service.java)
Su contenido o descripción

PASO 2 — Clasificación por tipo
Clasifica cada archivo en una de estas categorías:
A) Código fuente (Java, Python, TypeScript, JavaScript, Kotlin, etc.)
B) Configuración / documentación (YAML, properties, Markdown, JSON, txt, etc.)
C) Excel (.xlsx, .xls, .csv)
D) Word (.docx, .doc)
E) Otro tipo de archivo binario o especial
PASO 3 — Clasificación de errores en código fuente

Objetivo prioritario: que el proyecto compile. No corrijas flujo de negocio ni lógica funcional.

Antes de modificar cualquier archivo de código fuente, clasifica cada problema encontrado en una de estas dos categorías:
🔴 ERROR DE COMPILACIÓN — corregir siempre
Son errores que impiden que el proyecto arranque, sin valor pedagógico:

Import faltante o incorrecto
Clase, método o variable referenciada que no existe en ningún archivo del proyecto
Error de sintaxis
Anotación con atributos inválidos
Dependencia ausente en pom.xml, package.json, etc.
Archivo referenciado que no existe y debe ser creado con implementación mínima

→ CORREGIR estos errores.
🟡 PROBLEMA FUNCIONAL O DE CALIDAD — preservar siempre
Son problemas que no impiden compilar. Pueden ser intencionales para el aprendizaje:

Clave secreta hardcodeada ("secret", "password123")
API deprecada que funciona pero tiene reemplazo moderno
Lógica de negocio incorrecta o incompleta
Código redundante o de baja legibilidad
Falta de validaciones en flujo de negocio
Patrones de diseño incorrectos pero funcionales
Concurrencia no segura
Configuración funcional pero no óptima

→ PRESERVAR tal cual. No corregir, no mejorar, no comentar.
PASO 4 — Procesamiento según tipo de archivo
Tipo A — Código fuente
Aplica únicamente las correcciones clasificadas como 🔴 ERROR DE COMPILACIÓN.
No alteres ningún elemento clasificado como 🟡 PROBLEMA FUNCIONAL O DE CALIDAD.
Si falta un archivo referenciado, créalo con la implementación mínima necesaria para compilar.
Tipo B — Configuración / documentación
Extrae el contenido tal cual, sin modificaciones salvo errores evidentes de sintaxis
(ej: YAML mal indentado).
Tipo C — Excel (.xlsx)
Si viene con contenido real, genera el archivo respetando ese contenido.
Si viene con descripción en lenguaje natural, genera un archivo Excel funcional con:

Fila de encabezados en negrita con color de fondo distintivo
Columnas con ancho ajustado al contenido
Tipos de dato correctos por columna
Validaciones si la descripción lo indica
Hojas nombradas descriptivamente si hay más de una
Filas de ejemplo si no hay datos reales

Tipo D — Word (.docx)
Si viene con contenido real, genera el archivo respetando ese contenido.
Si viene con descripción en lenguaje natural, genera un documento Word funcional con:

Estilos de título (Título 1, Título 2) para jerarquía de secciones
Fuente legible (Calibri o equivalente), tamaño 11-12pt para cuerpo
Márgenes estándar
Tabla de contenido si tiene múltiples secciones
Tablas con encabezados en negrita si aplica

Tipo E — Otro
Genera el archivo con el contenido o estructura más apropiada según la descripción.
PASO 5 — Exportación en ZIP
Empaqueta todos los archivos en un único archivo ZIP descargable respetando exactamente
la estructura de rutas indicada por los marcadores.
El ZIP debe incluir:

Archivos de código con únicamente los errores de compilación corregidos
Archivos de configuración y documentación sin cambios
Archivos nuevos creados para resolver dependencias de compilación faltantes
Archivos Excel y Word generados desde descripción

IMPORTANTE: El ZIP debe estar listo para descargar al finalizar. No preguntes si el usuario
quiere generarlo. Simplemente genera el archivo y proporciona el enlace de descarga; No debes desplegar en el chat el resumen de lo que arreglaste al Zip, solo entregalo.

REGLAS IMPORTANTES

No omitas ningún archivo aunque no tenga errores ni modificaciones
Respeta los nombres y rutas exactas indicadas por los marcadores
Si un archivo no tiene marcador claro, infiere el nombre desde su contenido
Si la cadena contiene solo documentación, placeholders o binarios fake, NO la reproduzcas:
aplicá PASO 0 (materializar el proyecto del briefing). Reproducir la carcasa es un fallo.
No agregues texto después del enlace de descarga del ZIP
No preguntes si el usuario quiere el ZIP: simplemente generalo siempre
Si detectas que falta un archivo de configuración necesario para compilar
(pom.xml, package.json, requirements.txt, build.gradle, etc.), créalo e inclúyelo
inferiendo su contenido desde los imports y frameworks detectados en el código
Nunca corrijas problemas 🟡 aunque parezcan obvios o fáciles de mejorar.
El participante que recibirá este proyecto los debe encontrar y resolver él mismo.


INPUT
Aquí está la cadena con los archivos:

// === ARCHIVO: documentacion/diagnostico.md ===
# Diagnóstico: Estado Actual de la Activación de Clientes Nuevos

## Resumen Ejecutivo

El presente documento analiza la situación actual de la métrica de activación de clientes nuevos en la plataforma, identificando los principales indicadores de rendimiento, las brechas respecto a objetivos estratégicos y las oportunidades de mejora basadas en datos cuantitativos del último trimestre.

## 1. Contexto del Negocio

La empresa opera como plataforma B2B SaaS con un modelo de suscripción mensual. El crecimiento de la base de clientes en los últimos 12 meses ha sido del 45%, pasando de 12,500 a 18,150 clientes activos. Sin embargo, el equipo de producto ha identificado una preocupación crítica: la tasa de activación de clientes nuevos no ha seguido la misma tendencia positiva, lo cual representa un riesgo para la sostenibilidad del crecimiento.

El modelo de ingresos depende fundamentalmente de la retención de clientes, y los clientes que no se activan en los primeros 30 días tienen una probabilidad de churn del 73% en los siguientes 90 días. Por el contrario, los clientes que completan el flujo de activación tienen una retención del 89% al año. Esta diferencia representa un impacto económico sustancial: cada cliente activado genera un valor de vida (LTV) de USD 8,400 frente a USD 1,200 para clientes no activado.

## 2. Métrica Objetivo: Activación de Clientes Nuevos

### Definición Operacional

La activación de clientes nuevos se define como la proporción de cuentas creadas que completan al menos una acción de valor dentro de los primeros 30 días posteriores al registro. Se considera "acción de valor" cualquiera de las siguientes: creación de un proyecto, invite de al menos un miembro del equipo, configuración de integraciones, o generación del primer reporte.

### Estado Actual

| Indicador | Valor Actual | Objetivo | Brecha | Fuente |
|-----------|-------------|----------|--------|--------|
| Tasa de activación a 7 días | 34.2% | 50% | -15.8 pp | Analytics - Evento "activation_complete" |
| Tasa de activación a 30 días | 52.7% | 70% | -17.3 pp | Analytics - Evento "activation_complete" |
| Tiempo promedio hasta activación | 18.3 días | 12 días | +6.3 días | CRM - Timestamps de eventos |
| Clientes nuevos mensuales | 1,450 | 1,800 | -350 | Billing System |
| Costo de adquisición (CAC) | USD 485 | USD 420 | +15.5% | Marketing Analytics |

### Análisis de Cohortes

El análisis por cohorte de registro revela una tendencia preocupante: la tasa de activación ha disminuido consistentemente en las últimas seis cohortes mensuales, pasando del 61.2% en enero al 52.7% en junio. Esta caída de 8.5 puntos porcentuales en seis meses sugiere un cambio sistémico que requiere intervención.

Al segmentar por canal de adquisición, los datos muestran diferencias significativas: los clientes adquiridos por recomendación tienen una tasa de activación del 71.3%, mientras que los adquiridos por publicidad pagada apenas alcanzan el 41.8%. Los clientes inbound (content marketing) se sitúan en el 54.2%. Esta disparidad indica que la calidad del tráfico influye directamente en la activación, pero también sugiere oportunidades de mejora en el onboarding para todos los canales.

## 3. Análisis de los Factores de Activación

### Funnel de Activación

El análisis del funnel desde el registro hasta la activación completa revela dónde se producen las mayores fugas:

| Etapa del Funnel | Conversión | Fuga Acumulada | Insight |
|-----------------|------------|----------------|--------|
| Registro completado | 100% | 0% | Punto de partida |
| Email verificado | 87.3% | 12.7% | Fuga moderada |
| Primer login | 78.5% | 21.5% | Primera fricción significativa |
| Perfil completado | 62.1% | 37.9% | Alta fricción |
| Primer proyecto creado | 54.8% | 45.2% | Fuga crítica |
| Activación completa | 52.7% | 47.3% | Estado final |

La mayor pérdida se produce entre el registro y la activación completa, con casi la mitad de los clientes abandonando el proceso. Específicamente, la etapa de "perfil completado" a "primer proyecto creado" representa una fuga del 17.2%, indicando que los usuarios encuentran obstáculos para dar el primer paso activo en la plataforma.

### Segmentación por Variables Clave

El análisis por segmento de cliente muestra diferencias sustanciales en las tasas de activación:

- **Por tamaño de empresa**: Las empresas de 1-10 empleados tienen 58.3% de activación, mientras que las de más de 100 empleados apenas alcanzan el 38.5%. Esto sugiere que la complejidad organizacional introduce fricción.

- **Por industria**: Los sectores de tecnología (67.2%) y servicios profesionales (61.4%) muestran las tasas más altas, mientras que retail (42.1%) y manufactura (39.8%) están significativamente por debajo.

- **Por experiencia previa**: Clientes que han usado herramientas similares tienen 64.8% de activación versus 47.2% para usuarios sin experiencia previa.

- **Por dispositivo de registro**: El 71.3% de los registros desde desktop se activan, comparado con solo 31.2% desde mobile. Esta brecha de 40 puntos porcentuales es la más significativa.

## 4. Benchmarking y Referentes del Mercado

Para contextualizar el rendimiento, se comparó con benchmarks de la industria SaaS B2B:

| Percentil | Tasa de Activación (30 días) | Referencia |
|-----------|------------------------------|------------|
| 25th | 40% | Lower quartile |
| 50th | 55% | Median industry |
| 75th | 68% | Upper quartile |
| Nuestro valor | 52.7% | Por debajo de la mediana |

La empresa se sitúa por debajo de la mediana de la industria, lo cual confirma que existe espacio de mejora y que los objetivos propuestos son alcanzables.

## 5. Impacto Económico

La diferencia entre la tasa actual y el objetivo tiene implicaciones económicas directas:

- **Pérdida por sub-activación**: Con 1,450 clientes nuevos mensuales y una brecha de 17.3 puntos porcentuales frente al objetivo, la empresa deja de activar aproximadamente 251 clientes adicionales cada mes.

- **Impacto en ingresos**: Considerando el LTV diferenciado, esta brecha representa una pérdida mensual de ingresos potenciales por USD 2,107,400 (251 clientes × USD 8,400 LTV adicional) y una pérdida anual de USD 25,288,800.

- **Eficiencia del CAC**: Con un CAC de USD 485 y un LTV de clientes activados de USD 8,400, el ratio LTV:CAC actual es de 17.3:1 para clientes activados. Para clientes no activados, el ratio cae a 2.5:1, lo cual indica que el gasto en adquisición está siendo parcialmente desperdiciado.

## 6. Conclusiones del Diagnóstico

El análisis cuantitativo revela una situación que requiere intervención prioritaria: la tasa de activación de clientes nuevos se sitúa 17.3 puntos porcentuales por debajo del objetivo y por debajo de la mediana de la industria. Las principales áreas de fricción identificadas son la completarización del perfil, la creación del primer proyecto, y la experiencia móvil. El impacto económico de esta brecha es sustancial, con pérdidas potenciales de más de USD 25 millones anuales en ingresos por LTV.

La buena noticia es que las palancas de mejora son identificables y accionables. Las diferencias entre segmentos sugieren que intervenciones específicas por tipo de cliente y canal de adquisición pueden generar mejoras significativas con inversiones moderadas.

// === ARCHIVO: documentacion/arbol-de-metricas.md ===
# Árbol de Métricas: Activación de Clientes Nuevos

## Introducción y Metodología

Este documento presenta el árbol de métricas descompuesto desde la métrica objetivo de activación de clientes nuevos hasta las palancas accionables que el equipo puede impactar directamente. La metodología empleada sigue el marco de Objectives and Key Results (OKR) adaptado para análisis de producto, donde cada nivel superior se descompone en sus drivers subordinados hasta llegar a métricas operativas medibles.

El árbol distingue entre tres tipos de métricas: métricas de resultado (las que queremos optimizar), métricas de proceso (las que indican cómo vamos), y métricas de input (las que podemos controlar directamente). Esta distinción es fundamental para la priorización de iniciativas, ya que nos permite identificar palancas con diferentes horizontes de impacto.

## Nivel 1: Métrica Objetivo

**Tasa de Activación de Clientes Nuevos a 30 días**

- Definición: Porcentaje de cuentas creadas que completan al menos una acción de valor dentro de los primeros 30 días.
- Valor actual: 52.7%
- Objetivo: 70%
- Fuente: Analytics - Evento "activation_complete"
- Frecuencia de medición: Diaria, reportado semanalmente

Esta es la métrica norte del árbol. Todas las palancas identificadas en niveles inferiores deben demostrar correlación con esta métrica para ser consideradas válidas.

## Nivel 2: Drivers Principales

### 2.1 Tasa de Completion del Onboarding

La primera ramificación importante de la métrica objetivo es la tasa de completion del onboarding, que mide el porcentaje de usuarios que completan el flujo guiado de configuración inicial. Esta métrica captura la efectividad del proceso de bienvenida y setup inicial.

- Valor actual: 48.3%
- Objetivo: 65%
- Correlación con activación: 0.84 (alta)
- Fuente: Feature flag analytics - onboarding_flow_completion

**Descomposición de la tasa de completion:**

- Paso 1 - Verificación de email: 87.3%
- Paso 2 - Configuración de perfil: 72.1%
- Paso 3 - Invite de equipo: 61.5%
- Paso 4 - Primer proyecto: 54.8%
- Paso 5 - Integración de herramientas: 51.2%

### 2.2 Engagement Temprano

El segundo driver principal es el engagement temprano, que mide la intensidad del uso durante los primeros 7 días. Los datos históricos muestran una relación directa entre la frecuencia de uso en la primera semana y la probabilidad de activación.

- Valor actual: 2.3 sesiones por usuario en primera semana
- Objetivo: 4.0 sesiones
- Correlación con activación: 0.79 (alta)
- Fuente: Analytics - session_events

**Métricas de engagement desglosadas:**

- Duración promedio de sesión: 8.4 minutos (objetivo: 12 minutos)
- Features utilizados en primera semana: 2.1 (objetivo: 4.0)
- Días activos en primera semana: 3.2 (objetivo: 5.0)

### 2.3 Tasa de Activación Temprana (7 días)

Este driver captura la velocidad de activación, reconociendo que los usuarios que se activan más rápido tienen mayor probabilidad de permanecer activos a largo plazo.

- Valor actual: 34.2%
- Objetivo: 50%
- Correlación con activación a 30 días: 0.91 (muy alta)
- Fuente: Analytics - activation_event por ventana de 7 días

## Nivel 3: Palancas Accionables

### 3.1 Reducción de Fricción en Onboarding

Esta palanca agrupa todas las iniciativas orientadas a eliminar obstáculos en el proceso de configuración inicial. Los datos del funnel muestran que la mayor fuga ocurre entre el registro y la creación del primer proyecto.

**Métricas operativas:**

- Tiempo para completar onboarding: 14.2 minutos (objetivo: 8 minutos)
- Número de pasos en onboarding: 5 (objetivo: 3)
- Tasa de abandono por paso: 18.2% promedio (objetivo: <10%)

**Iniciativas identificadas:**

- Implementar onboarding adaptativo basado en perfil de usuario
- Reducir campos requeridos en registro inicial
- Añadir tooltips contextuales durante primer uso
- Habilitar importación de datos desde herramientas similares

### 3.2 Mejora de la Experiencia Móvil

La brecha de 40 puntos porcentuales entre activación desde desktop y mobile representa una oportunidad significativa. Esta palanca aborda específicamente las mejoras en la experiencia móvil.

**Métricas operativas:**

- Tasa de activación desde mobile: 31.2% (objetivo: 50%)
- Puntuación de usabilidad móvil (NPS de producto): 23 (objetivo: 45)
- Tasa de completación de tareas críticas en móvil: 41.8% (objetivo: 65%)

**Iniciativas identificadas:**

- Rediseñar interfaz móvil para flujos principales
- Implementar modo offline para funciones básicas
- Optimizar tiempos de carga en móvil (actualmente 4.8s, objetivo <2s)
- Añadir notificaciones push para re-engagement

### 3.3 Programa de Activación Proactiva

Esta palanca se enfoca en intervenciones activas para acelerar la activación, tanto automatizadas como asistidas por el equipo de éxito del cliente.

**Métricas operativas:**

- Tiempo hasta primer contacto del CSM: 12.4 días (objetivo: 3 días)
- Tasa de respuesta a emails de onboarding: 23.4% (objetivo: 40%)
- Clientes con onboarding call agendada: 18.2% (objetivo: 50%)

**Iniciativas identificadas:**

- Implementar email series de activación con contenido personalizado
- Crear checklist de activación visible en dashboard
- Establecer alertas para usuarios en riesgo de no activación
- Ofrecer sesiones de onboarding grupales

### 3.4 Optimización por Segmento

Reconociendo las diferencias significativas entre segmentos, esta palanca aborda la personalización del onboarding según características del cliente.

**Métricas operativas:**

- Tasa de activación por segmento vs objetivo:
  - Enterprise (>100 empleados): 38.5% / 55% = 0.70
  - Mid-market (11-100): 54.2% / 65% = 0.83
  - SMB (1-10): 58.3% / 75% = 0.78

**Iniciativas identificadas:**

- Desarrollar onboarding específico para segmento enterprise
- Crear templates de proyecto por industria
- Implementar integraciones prioritarias por segmento
- Personalizar comunicaciones según perfil de usuario

## Nivel 4: Métricas de Input

### 4.1 Métricas de Producto

- Velocidad de carga de página inicial: 2.8s (objetivo: <1.5s)
- Número de errores en flujo de onboarding: 1.2% (objetivo: <0.5%)
- Disponibilidad de funcionalidades críticas: 99.2% (objetivo: 99.9%)
- Cobertura de documentación: 67% (objetivo: 90%)

### 4.2 Métricas de Marketing y Ventas

- Calidad de leads (porcentaje que se activa): 41.8% (objetivo: 55%)
- Alineación entre promesa de venta y experiencia: 3.2/5 (objetivo: 4.5/5)
- Tiempo de respuesta a inquiries de pre-onboarding: 4.2h (objetivo: <1h)

### 4.3 Métricas de Customer Success

- Ratio de CSM por cliente: 1:85 (objetivo: 1:50)
- Tiempo medio de resolución de issues de onboarding: 18.4h (objetivo: <8h)
- NPS de onboarding: 34 (objetivo: 50)

## Validación del Árbol

Para validar la integridad del árbol de métricas, se realizó un análisis de correlación entre las métricas de nivel 3 y la métrica objetivo. Los coeficientes de correlación se calcularon utilizando datos de los últimos 6 meses con granularidad semanal:

| Palanca | Correlación | Significancia |
|---------|-------------|---------------|
| Reducción de fricción en onboarding | 0.84 | p<0.001 |
| Mejora de experiencia móvil | 0.71 | p<0.01 |
| Programa de activación proactiva | 0.76 | p<0.01 |
| Optimización por segmento | 0.68 | p<0.05 |

Todas las palancas muestran correlaciones estadísticamente significativas, lo cual valida la estructura del árbol. Adicionalmente, se verificó que las métricas de nivel 4 tienen correlación con sus palancas padre, asegurando que los inputs se traducen en outcomes.

// === ARCHIVO: documentacion/plan-de-accion.md ===
# Plan de Acción: Iniciativas para Aumentar la Activación de Clientes Nuevos

## Resumen del Plan

Este documento detalla el plan de acción para las iniciativas priorizadas basadas en el árbol de métricas y la matriz de priorización. Cada iniciativa incluye objetivos específicos, métricas de éxito, cronograma de implementación, recursos asignados y criterios de evaluación. El plan contempla un horizonte de 6 meses con revisiones mensuales para ajustar basado en datos reales.

## Iniciativa 1: Rediseño del Flujo de Onboarding

### Descripción
Rediseñar el flujo de onboarding para reducir el número de pasos requeridos, implementar un proceso adaptativo basado en el perfil del usuario, y añadir elementos de gamificación que incentiven la progresión.

### Dueño
Product Manager - Onboarding (María González)

### Plazo
- Inicio: Semana 1
- Primera versión: Semana 6
- Iteración completa: Semana 12

### Recursos Asignados
- 1 Product Manager (40% del tiempo)
- 1 UX Designer (80% del tiempo)
- 2 Frontend Engineers (100% del tiempo)
- 1 Data Analyst (20% del tiempo)

### Inversión Estimada
USD 85,000 (incluye desarrollo, herramientas de analítica y测试)

### Métricas de Éxito
- Tasa de completion del onboarding: de 48.3% a 60% (dentro de 12 semanas)
- Tiempo para completar onboarding: de 14.2 a 10 minutos
- Tasa de activación a 30 días: impacto estimado de +4 puntos porcentuales

### Criterio de Éxito
La iniciativa se considera exitosa si, tras 12 semanas de implementación, la tasa de activación a 30 días muestra una mejora estadísticamente significativa (p<0.05) de al menos 4 puntos porcentuales respecto a la línea base.

### Hitos
1. Semana 2: Entregable de investigación de usuarios y diseño de flujos
2. Semana 4: Mockups y prototipos validados con usuarios
3. Semana 6: MVP del nuevo onboarding desplegado a 20% de usuarios
4. Semana 8: Análisis de resultados del MVP y ajustes
5. Semana 12: Despliegue al 100% y validación de impacto

## Iniciativa 2: Optimización Mobile-First

### Descripción
Rediseñar la experiencia móvil para que las funcionalidades principales sean plenamente operativas y usables, con especial énfasis en el flujo de activación (registro, perfil, primer proyecto).

### Dueño
Engineering Lead - Mobile (Carlos Ramírez)

### Plazo
- Inicio: Semana 2
- MVP funcional: Semana 8
- Release completo: Semana 14

### Recursos Asignados
- 1 Engineering Lead (50% del tiempo)
- 2 Mobile Engineers (100% tiempo completo)
- 1 QA Engineer (50% del tiempo)
- 1 UX Designer (40% del tiempo)

### Inversión Estimada
USD 120,000 (desarrollo, testing, optimización de rendimiento)

### Métricas de Éxito
- Tasa de activación desde móvil: de 31.2% a 45%
- Tiempo de carga en móvil: de 4.8s a <2s
- Puntuación de usabilidad móvil: de 23 a 40

### Criterio de Éxito
La iniciativa es exitosa si la tasa de activación desde dispositivos móviles mejora en al menos 10 puntos porcentuales dentro de las 14 semanas posteriores al lanzamiento, con una mejora adicional de 4 puntos porcentuales en los siguientes 30 días.

### Hitos
1. Semana 3: Auditoría de experiencia móvil actual
2. Semana 5: Diseño de nuevos flujos mobile
3. Semana 8: MVP con flujos principales optimizados
4. Semana 11: Beta testing con usuarios seleccionados
5. Semana 14: Lanzamiento oficial y monitoreo

## Iniciativa 3: Programa de Activación Automatizada

### Descripción
Implementar un sistema automatizado de emails, notificaciones in-app y alertas para identificar usuarios en riesgo de no activación y activar intervenciones proactivas.

### Dueño
Growth Lead (Ana Martínez)

### Plazo
- Inicio: Semana 1
- Sistema de segmentación: Semana 4
- Campañas activas: Semana 6
- Optimización continua: ongoing

### Recursos Asignados
- 1 Growth Lead (60% del tiempo)
- 1 Marketing Automation Specialist (80% del tiempo)
- 1 Backend Engineer (40% del tiempo)
- 1 Data Analyst (30% del tiempo)

### Inversión Estimada
USD 45,000 (herramientas de automation, desarrollo de integraciones, contenido)

### Métricas de Éxito
- Tasa de apertura de emails de onboarding: de 23.4% a 35%
- Tasa de conversión a activación por email: de 8.2% a 15%
- Reducción del tiempo hasta activación: de 18.3 a 14 días

### Criterio de Éxito
El programa es exitoso si el sistema automatizado genera una mejora de al menos 3 puntos porcentuales en la tasa de activación a 30 días, con un costo por activación menor a USD 15.

### Hitos
1. Semana 2: Definición de segmentos y triggers
2. Semana 4: Sistema de scoring de riesgo implementado
3. Semana 6: Primera campaña de emails activa
4. Semana 8: Notificaciones in-app desplegadas
5. Semana 10: Optimización basada en datos de primeras campañas

## Iniciativa 4: Onboarding Personalizado por Segmento

### Descripción
Desarrollar experiencias de onboarding diferenciadas para los segmentos Enterprise, Mid-market y SMB, incluyendo contenido, integraciones y flujos específicos.

### Dueño
Director de Customer Success (Roberto Lee)

### Plazo
- Inicio: Semana 3
- Desarrollo de contenido: Semana 8
- Despliegue por segmento: Semana 10
- Completado: Semana 14

### Recursos Asignados
- 1 Director de CS (30% del tiempo)
- 1 Customer Success Manager (60% del tiempo)
- 1 Content Specialist (80% del tiempo)
- 1 Product Manager (20% del tiempo)

### Inversión Estimada
USD 35,000 (contenido, formación de equipo CS, herramientas de personalización)

### Métricas de Éxito
- Tasa de activación Enterprise: de 38.5% a 50%
- Tasa de activación Mid-market: de 54.2% a 62%
- NPS de onboarding: de 34 a 45

### Criterio de Éxito
La iniciativa es exitosa si cada segmento muestra una mejora de al menos 8 puntos porcentuales en su tasa de activación dentro de las 14 semanas posteriores al lanzamiento.

### Hitos
1. Semana 4: Mapeo de necesidades por segmento
2. Semana 6: Desarrollo de contenido específico
3. Semana 8: Creación de templates y configuraciones
4. Semana 10: Piloto con segmento Enterprise
5. Semana 14: Despliegue a todos los segmentos

## Cronograma Consolidado

| Iniciativa | Q1 | Q2 | Responsable |
|------------|----|----|-------------|
| Rediseño de Onboarding | ████████ | ██ | María González |
| Optimización Mobile | ████████ | ██ | Carlos Ramírez |
| Activación Automatizada | ████████████ | ██ | Ana Martínez |
| Onboarding por Segmento | ████████ | | Roberto Lee |

## Gestión de Riesgos

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Retrasos en desarrollo de onboarding | Media | Alto | Priorizar MVP y iterar |
| Resistencia al cambio en usuarios existentes | Media | Medio | Comunicación proactiva y feature flags |
| Recursos de ingeniería no disponibles | Alta | Alto | Priorizar iniciativas con recursos asegurados |
| Resultados de móvil menores a esperados | Baja | Alto | Testing exhaustivo y ajustes rápidos |

## Presupuesto Total

| Iniciativa | Inversión (USD) | % del Total |
|------------|-----------------|-------------|
| Rediseño de Onboarding | 85,000 | 27% |
| Optimización Mobile | 120,000 | 38% |
| Activación Automatizada | 45,000 | 14% |
| Onboarding por Segmento | 35,000 | 11% |
| Contingencia (10%) | 28,500 | 9% |
| **Total** | **313,500** | **100%** |

## Proceso de Revisión

El plan se revisará mensualmente con el siguiente proceso:

1. **Recolección de datos**: Durante la primera semana de cada mes, el equipo de analytics compila los datos de todas las métricas de éxito.

2. **Análisis de resultados**: En la segunda semana, cada dueño de iniciativa presenta un análisis de progreso al equipo de liderazgo.

3. **Decisiones de ajuste**: En la tercera semana, se toman decisiones sobre continuer, pivotar o detener iniciativas basadas en los datos.

4. **Comunicación**: En la cuarta semana, se comparte un resumen de progreso con stakeholders relevantes.

El plan contempla un punto de decisión formal al final del Q1 (semana 12) donde se evaluará el rendimiento de todas las iniciativas y se ajustará el presupuesto y prioridades para Q2 basándose en los resultados obtenidos.

// === ARCHIVO: documentacion/recomendacion.md ===
# Recomendación Final: Estrategia de Activación de Clientes Nuevos

## Resumen Ejecutivo

Después de un análisis exhaustivo del árbol de métricas, la evaluación de iniciativas y el modelado cuantitativo, la recomendación estratégica es implementar un programa integrado de cuatro iniciativas que, en conjunto, proyectan mejorar la tasa de activación de clientes nuevos del 52.7% actual al 70% objetivo en un horizonte de 6 meses. Esta mejora representa un impacto económico potencial de USD 18.7 millones anuales en ingresos incrementales por LTV.

La recomendación se fundamenta en datos cuantitativos, análisis de correlación entre palancas y resultados esperados, y considera las restricciones de recursos y el contexto competitivo actual.

## Recomendación Principal

Se recomienda ejecutar las siguientes iniciativas en el orden de prioridad indicado:

**Prioridad 1 (Iniciar Semana 1):** Programa de Activación Automatizada
- Justificación: Menor inversión (USD 45,000), implementación más rápida (6 semanas), y mayor alcance inmediato. El sistema de segmentación y automatización puede beneficiar a todos los segmentos de clientes simultáneamente.
- ROI proyectado: 847% en 12 meses

**Prioridad 2 (Iniciar Semana 1):** Rediseño del Flujo de Onboarding
- Justificación: Impacto directo en la principal fricción identificada (conversión de registro a primer proyecto). La correlación de 0.84 con la métrica de activación es la más alta entre todas las palancas.
- ROI proyectado: 423% en 12 meses

**Prioridad 3 (Iniciar Semana 2):** Optimización Mobile-First
- Justificación: Aborda la brecha más significativa entre segmentos (40 puntos porcentuales entre desktop y mobile). Aunque requiere mayor inversión, el mercado móvil representa el 35% de los registros actuales y está subatendido.
- ROI proyectado: 312% en 12 meses

**Prioridad 4 (Iniciar Semana 3):** Onboarding Personalizado por Segmento
- Justificación: Maximiza el impacto en segmentos de alto valor (Enterprise). Complementa las otras iniciativas añadiendo personalización. Puede implementarse con recursos existentes de Customer Success.
- ROI proyectado: 567% en 12 meses

## Alternativas Consideradas

### Alternativa A: Solo Mejoras de Producto

Esta alternativa contemplaba únicamente inversiones en producto (onboarding y mobile) sin componente de automatización ni personalización.

- Inversión estimada: USD 205,000
- Impacto proyectado en activación: +10.3 puntos porcentuales
- ROI proyectado: 298% en 12 meses

**Razón de descarte:** Si bien tiene un ROI atractivo, el impacto absoluto no alcanza el objetivo del 70%. Además, esta alternativa no aprovecha la oportunidad de mejora en segmentos de alto valor y depende exclusivamente de cambios en el producto, sin intervención en la experiencia post-registro.

### Alternativa B: Programa Masivo de Customer Success

Esta alternativa priorizaba la contratación de más agentes de CS para ofrecer onboarding asistido a todos los clientes nuevos.

- Inversión estimada: USD 280,000 (incluyendo contratación y formación)
- Impacto proyectado en activación: +8.7 puntos porcentuales
- ROI proyectado: 187% en 12 meses

**Razón de descarte:** El ROI es significativamente menor que las otras alternativas debido al alto costo operativo recurrente. Además, la escalabilidad es limitada y no escala proporcionalmente con el crecimiento de clientes. El modelo asistido no es sostenible para el objetivo de crecimiento del 45% anual.

### Alternativa C: Solo Automatización y Email

Esta alternativa se enfocaba exclusivamente en marketing automation sin cambios en el producto.

- Inversión estimada: USD 28,000
- Impacto proyectado en activación: +5.2 puntos porcentuales
- ROI proyectado: 612% en 12 meses

**Razón de descarte:** Aunque tiene el mayor ROI, el impacto absoluto es insuficiente. Los datos muestran que la automatización sola no puede compensar las fricciones de producto identificadas. Esta alternativa podría implementarse como complemento pero no como estrategia principal.

### Alternativa D: Enfoque Exclusivo en Enterprise

Esta alternativa priorizaba el segmento Enterprise con recursos dedicados y atención personalizada.

- Inversión estimada: USD 150,000
- Impacto proyectado en activación Enterprise: +20 puntos porcentuales
- Impacto global: +4.8 puntos porcentuales
- ROI proyectado: 145% en 12 meses

**Razón de descarte:** Si bien el segmento Enterprise tiene el mayor LTV, el impacto global es insuficiente y el ROI es menor que otras alternativas. Además, esta alternativa ignora el volumen significativo de clientes SMB y Mid-market que representan el 73% de la base.

## Justificación de la Selección

La recomendación de implementar las cuatro iniciativas en paralelo se basa en tres factores clave:

**1. Complementariedad de las iniciativas:** Los análisis de correlación muestran que las cuatro palancas impactan la métrica de activación de manera independiente. La combinación de mejoras de producto (onboarding, mobile) con intervenciones de engagement (automatización, personalización) tiene un efecto sinérgico mayor que la suma de sus partes. El modelo cuantitativo proyecta un efecto multiplicador de 1.3x cuando se implementan juntas versus secuencialmente.

**2. Distribución de riesgo:** Al diversificar las iniciativas entre producto, tecnología y operaciones, se reduce el riesgo de dependencia de un solo vector de mejora. Si una iniciativa no alcanza los resultados esperados, las otras pueden compensar parcialmente.

**3. Escalabilidad futura:** Las cuatro iniciativas construyen capacidades reutilizables: el sistema de automatización puede extenderse a otras métricas (engagement, retención), el nuevo onboarding puede adaptarse a futuros segmentos, y las optimizaciones móviles benefician a toda la base de usuarios.

## Análisis de Sensibilidad

El modelo quantitativo incluye un análisis de sensibilidad considerando tres escenarios:

| Escenario | Supuestos Clave | Activación Final | Ingresos Incrementales |
|-----------|-----------------|------------------|----------------------|
| Conservador | Solo 60% de efectividad de iniciativas | 63.1% | USD 12.4M |
| Base | 100% de efectividad proyectada | 70.0% | USD 18.7M |
| Optimista | 130% de efectividad (efecto viral) | 73.8% | USD 24.9M |

El escenario conservador sigue representando un retorno positivo (343% ROI), lo cual hace la inversión robusta ante posibles desviaciones.

## Recomendaciones Adicionales

Más allá de las cuatro iniciativas principales, se recomienda considerar las siguientes acciones complementarias:

**Corto plazo (0-3 meses):**
- Establecer un dashboard de métricas de activación con actualización diaria
- Implementar weekly reviews del equipo de producto y growth
- Crear un proceso de feedback loop con clientes que no se activan

**Mediano plazo (3-6 meses):**
- Evaluar la implementación de un programa de referidos para clientes activados
- Desarrollar un programa de beta testers entre clientes nuevos
- Invertir en contenido educativo y certificaciones

**Largo plazo (6-12 meses):**
- Explorar partnerships con herramientas complementarias para ofrecer integraciones out-of-the-box
- Desarrollar comunidad de usuarios para generar engagement peer-to-peer
- Evaluar expansión del modelo de activación a otros flujos (upsell, cross-sell)

## Conclusión

La recomendación de implementar las cuatro iniciativas identificadas representa la estrategia óptima para alcanzar el objetivo de activación del 70% con un ROI atractivo y un perfil de riesgo razonable. La inversión total de USD 313,500 proyecta un retorno de USD 18.7 millones anuales, equivalente a un ROI del 597%.

El plan se revisará mensualmente para ajustar basado en datos reales, con un punto de decisión formal al final del Q1. La clave del éxito será la ejecución disciplinada y la capacidad de iterar rápidamente basándose en los aprendizajes del mercado.

// === ARCHIVO: documentacion/matriz-priorizacion.md ===
# Matriz de Priorización: Iniciativas de Activación de Clientes Nuevos

## Metodología de Priorización

La priorización de iniciativas se realizó utilizando una matriz de impacto-esfuerzo con criterios cuantificables. Cada iniciativa fue evaluada en cinco dimensiones: impacto en la métrica de activación, impacto en ingresos, esfuerzo de implementación, tiempo de implementación, y riesgo de ejecución. Los criterios de evaluación fueron definidos por el equipo de liderazgo y validados con datos históricos de proyectos similares.

La escala de impacto y esfuerzo utiliza valores del 1 al 5, donde 1 representa el mínimo impacto o esfuerzo, y 5 el máximo. El score final de priorización se calcula como: (Impacto Promedio × 0.4) + (ROI Relativo × 0.3) + (Urgencia × 0.2) + (Facilidad × 0.1).

## Matriz de Priorización

| Iniciativa | Impacto (1-5) | Esfuerzo (1-5) | ROI (%) | Urgencia (1-5) | Facilidad (1-5) | Score Final | Prioridad |
|------------|---------------|-----------------|---------|----------------|-----------------|-------------|-----------|
| Programa de Activación Automatizada | 4.0 | 2.0 | 847% | 5.0 | 4.0 | 4.35 | 1 |
| Rediseño del Flujo de Onboarding | 4.5 | 3.0 | 423% | 4.5 | 3.5 | 4.08 | 2 |
| Optimización Mobile-First | 3.5 | 4.0 | 312% | 4.0 | 2.5 | 3.30 | 3 |
| Onboarding Personalizado por Segmento | 3.0 | 2.5 | 567% | 3.5 | 4.0 | 3.28 | 4 |

## Detalle de Evaluaciones

### Programa de Activación Automatizada
- **Impacto**: 4.0/5.0 - Impacto alto en la tasa de activación a través de intervención proactiva. Afecta directamente el driver de engagement temprano con correlación de 0.76.
- **Esfuerzo**: 2.0/5.0 - Bajo esfuerzo relativo. Utiliza herramientas existentes de marketing automation y requiere desarrollo moderado de integraciones.
- **ROI**: 847% - El más alto de todas las iniciativas. Baja inversión con impacto inmediato y escalable.
- **Urgencia**: 5.0/5.0 - Máxima urgencia. Es la única iniciativa que puede implementarse inmediatamente y comenzar a generar impacto en semanas.
- **Facilidad**: 4.0/5.0 - Alta facilidad de implementación. No requiere cambios en el producto core y puede desplegarse gradualmente.

### Rediseño del Flujo de Onboarding
- **Impacto**: 4.5/5.0 - Impacto muy alto. La correlación más fuerte (0.84) con la métrica de activación justifica esta calificación.
- **Esfuerzo**: 3.0/5.0 - Esfuerzo moderado. Requiere diseño, desarrollo y testing pero dentro de capacidades del equipo actual.
- **ROI**: 423% - ROI atractivo considerando el impacto alto.
- **Urgencia**: 4.5/5.0 - Alta urgencia. La fricción en onboarding es el principal obstáculo identificado.
- **Facilidad**: 3.5/5.0 - Facilidad moderada. Requiere coordinación entre diseño y desarrollo, pero es un proyecto bien definido.

### Optimización Mobile-First
- **Impacto**: 3.5/5.0 - Impacto significativo pero concentrado en un segmento (usuarios móviles). La brecha de 40pp justifica el impacto.
- **Esfuerzo**: 4.0/5.0 - Alto esfuerzo. Requiere desarrollo nativo significativo y testing exhaustivo en múltiples dispositivos.
- **ROI**: 312% - ROI bueno pero el más bajo de las cuatro iniciativas.
- **Urgencia**: 4.0/5.0 - Alta urgencia. La experiencia móvil actual está dañando la percepción de marca.
- **Facilidad**: 2.5/5.0 - Baja facilidad. Complejidad técnica y necesidad de testing extensivo.

### Onboarding Personalizado por Segmento
- **Impacto**: 3.0/5.0 - Impacto moderado pero con potencial de personalización para segmentos de alto valor.
- **Esfuerzo**: 2.5/5.0 - Esfuerzo bajo-moderado. Mayormente contenido y configuración, no desarrollo heavy.
- **ROI**: 567% - ROI alto. Bajo costo con impacto focalizado en segmentos de alto valor.
- **Urgencia**: 3.5/5.0 - Urgencia moderada. Complementa otras iniciativas pero no es crítica por sí sola.
- **Facilidad**: 4.0/5.0 - Alta facilidad. Puede implementarse con recursos existentes de CS y contenido.

## Distribución de Recursos Propuesta

Basándose en la priorización, la distribución recomendada del presupuesto total (USD 313,500) es:

| Iniciativa | Presupuesto | % del Total | Justificación |
|------------|-------------|-------------|----------------|
| Programa de Activación Automatizada | USD 45,000 | 14% | Menor inversión, mayor ROI, implementación rápida |
| Rediseño del Flujo de Onboarding | USD 85,000 | 27% | Segundo mayor impacto, alta correlación con objetivo |
| Optimización Mobile-First | USD 120,000 | 38% | Mayor inversión justificada por brecha significativa |
| Onboarding Personalizado por Segmento | USD 35,000 | 11% | Complementa otras iniciativas, bajo costo |
| Contingencia | USD 28,500 | 9% | Reserva para ajustes y oportunidades emergentes |

## Gráfico de Priorización (Texto)

```
Impacto ↑
  5 │                    [Onboarding]
  4 │      [Automatización]  ▓▓▓▓▓▓▓▓▓▓▓▓
  3 │      ▓▓▓▓▓▓▓▓▓▓▓▓      ▓▓▓▓▓▓▓▓▓▓▓▓
  2 │      ▓▓▓▓▓▓▓▓▓▓▓▓      ▓▓▓▓▓▓▓▓▓▓▓▓
  1 │      ▓▓▓▓▓▓▓▓▓▓▓▓      ▓▓▓▓▓▓▓▓▓▓▓▓
  0 └─────────────────────────────────────────→ Esfuerzo
      1    2    3    4    5
```

Leyenda:
- [Automatización]: Programa de Activación Automatizada (Alto impacto, bajo esfuerzo)
- [Onboarding]: Rediseño del Flujo de Onboarding (Alto impacto, esfuerzo moderado)
- ▓▓▓ Mobile: Optimización Mobile-First (Impacto moderado, alto esfuerzo)
- ▓▓▓ Segmento: Onboarding Personalizado por Segmento (Impacto moderado, bajo esfuerzo)

## Criterios de Éxito por Iniciativa

| Iniciativa | Métrica Principal | Target | Deadline |
|------------|------------------|--------|----------|
| Automatización | Tasa de activación | +3pp | Semana 10 |
| Onboarding | Completion rate | 60% | Semana 12 |
| Mobile | Activación móvil | 45% | Semana 14 |
| Segmento | Activación Enterprise | 50% | Semana 14 |

## Revisión y Repriorización

La matriz de priorización es un documento vivo que se revisará:

- **Semanal**: Monitoreo de métricas de progreso de cada iniciativa
- **Mensual**: Revisión formal de scores y ajustes si hay cambios en contexto
- **Trimestral**: Reevaluación completa de priorización basada en resultados

Los criterios para repriorizar incluyen: cambio significativo en recursos disponibles, nuevos datos de mercado, cambios en estrategia corporativa, o desviaciones mayores a ±20% en los resultados proyectados.

// === ARCHIVO: modelos/hipotesis.csv ===
id_hipotesis,palanca,descripcion,impacto_estimado,esfuerzo_estimado,forma_validacion,supuestos,estado,fecha_creacion
H1,Reduccion de friccion en onboarding,La reduccion del numero de pasos en el onboarding de 5 a 3 incrementara la tasa de completion en un 25%,lo que se traducira en una mejora de 4.5 puntos porcentuales en la tasa de activacion a 30 dias,4,3,Test A/B con grupo de control: 50% usuarios con onboarding reducido vs 50% con actual. Medir tasa de activacion a 30 dias despues de 8 semanas.,El tiempo de implementacion es de 6 semanas. La muestra minima por grupo es de 500 usuarios para significancia estadistica.,activa,2025-01-15
H2,Onboarding adaptativo,Un onboarding que se adapta al perfil del usuario (segmento, industria, tamano de empresa) incrementara la relevancia percibida y reducira el tiempo hasta la activacion,3.5,4,Test A/B: 20% de usuarios con onboarding adaptativo vs 80% con actual. Medir tiempo hasta activacion y tasa final.,El sistema de segmentacion esta disponible. Los perfiles de usuario tienen suficientes datos para personalizar.,activa,2025-01-15
H3,Optimizacion de experiencia movil,La mejora de la experiencia movil (tiempo de carga, usabilidad, funcionalidad) incrementara la tasa de activacion desde dispositivos moviles de 31.2% a 45%,4,4.5,Medir tasa de activacion por dispositivo antes y despues del rediseño. Comparar cohorts de 4 semanas pre y post lanzamiento.,El 35% de registros viene de mobile. La mejora de velocidad es tecnicamente viable.,activa,2025-01-15
H4,Notificaciones push de re-engagement,El envio de notificaciones push personalizadas en dias 3, 7 y 14 incrementara la tasa de activacion a 30 dias en 2.5 puntos porcentuales,3,2,Test A/B: Grupo con notificaciones vs grupo sin. Medir tasa de activacion y dias hasta activacion.,La tasa de opt-in para notificaciones es mayor al 60%. El contenido de notificaciones es relevante.,activa,2025-01-15
H5,Email series de activacion,Una serie de 5 emails de activacion con contenido personalizado incrementara la tasa de apertura en 40% y la conversions en 8%,3.5,2,Medir tasa de apertura, click-through, y conversion a activacion. Comparar con periodo anterior.,Los emails se entregan en el momento optimo del customer journey. El contenido es relevante.,activa,2025-01-15
H6,Onboarding asistido para Enterprise,Ofrecer una llamada de onboarding dedicada a clientes Enterprise incrementara su tasa de activacion de 38.5% a 55%,4,3,Medir tasa de activacion de clientes Enterprise con vs sin onboarding asistido. Comparar cohorts de 3 meses.,Los clientes Enterprise valoran la atencion personalizada. El equipo de CS tiene capacidad.,activa,2025-01-15
H7,Gamificacion del onboarding,La adicion de elementos de gamificacion (progresion, badges, puntos) incrementara el engagement en el onboarding en un 30%,3,3.5,Test A/B: 20% usuarios con gamificacion vs 80% sin. Medir completion rate y tiempo en plataforma.,Los usuarios responden positivamente a gamificacion. El desarrollo es factible en el timeline.,activa,2025-01-15
H8,Integraciones prioritarias por industria,Ofrecer integraciones pre-configuradas por industria incrementara la percepcion de valor y la activacion en ese segmento,3.5,3,Medir tasa de activacion por industria antes y despues de implementar integraciones especificas.,Las industrias objetivo tienen necesidades de integracion identificables. Las integraciones son tecnicamente viables.,activa,2025-01-15
H9,Alertas de riesgo de no activacion,Un sistema de scoring que identifique usuarios en riesgo de no activacion y active intervenciones proactivas mejorara la tasa global en 3 puntos porcentuales,4,2.5,Medir tasa de conversion de usuarios en riesgo que recibieron intervencion vs los que no.,El modelo de scoring tiene precision mayor al 70%. Las intervenciones son efectivas.,activa,2025-01-15
H10,Contenido educativo en onboarding,La inclusion de tutoriales interactivos y contenido educativo contextual incrementara la tasa de completacion del onboarding en un 20%,2.5,2,Medir tasa de completacion y activacion con vs sin contenido educativo.,El contenido es de alta calidad y relevante. Los usuarios tienen tiempo para consumirlo.,activa,2025-01-15

// === ARCHIVO: modelos/modelo.csv ===
parametro,valor,fuente,supuesto,escenario_conservador,escenario_base,escenario_optimista,notas
clientes_nuevos_mensuales,1450,CRM - ultimo mes,Volumen constante de nuevos clientes,1300,1450,1600,Proyeccion basada en tendencia de 12 meses
tasa_activacion_actual,52.7%,Analytics - 30 dias,Linea base medida,52.7%,52.7%,52.7%,Promedio movil de 3 meses
tasa_activacion_objetivo,70%,Objetivo estrategico,Meta del negocio,63%,70%,73%,Tres escenarios de consecucion
brecha_puntos_porcentuales,17.3,Calculo,Diferencia entre actual y objetivo,10.3,17.3,21.1,Base del calculo de impacto
clientes_adicionales_activados_mensuales,251,Calculo,Clientes nuevos × brecha,149,251,306,Impacto directo mensual
ltv_cliente_activado,8400,Finance,Valor de vida promedio,8400,8400,8400,Basado en historial de 24 meses
ltv_cliente_no_activado,1200,Finance,Valor de clientes que no se activan,1200,1200,1200,Churn a 90 dias
diferencial_ltv_por_cliente,7200,Calculo,LTV activado - LTV no activado,7200,7200,7200,Beneficio por cliente activado
ingresos_mensuales_incrementales,1807200,Calculo,Clientes adicionales × diferencial LTV,1072800,1807200,2203200,Beneficio mensual proyectado
ingresos_anuales_incrementales,21686400,Calculo,Ingresos mensuales × 12,12873600,21686400,26438400,Beneficio anual proyectado
inversion_total_iniciativas,313500,Plan de accion,Presupuesto total del programa,313500,313500,313500,Inversion en 6 meses
roi_porcentaje,6819%,Calculo,(Ingresos - Inversion) / Inversion × 100,4005%,6819%,8261%,Retorno sobre inversion
payback_meses,0.2,Calculo,Inversion / Ingresos mensuales,0.3,0.2,0.1,Meses para recuperar inversion
tasa_activacion_automatizacion,55.7%,Estimacion,Impacto de H4 y H5,53.5%,55.7%,57.5%,Mejora por automation
tasa_activacion_onboarding,57.2%,Estimacion,Impacto de H1 y H2,54.5%,57.2%,59.5%,Mejora por onboarding
tasa_activacion_mobile,56.9%,Estimacion,Impacto de H3,54.0%,56.9%,58.8%,Mejora por mobile
tasa_activacion_segmento,55.4%,Estimacion,Impacto de H6 y H8,53.8%,55.4%,57.0%,Mejora por personalizacion
efecto_multiplicador,1.3,Estimacion,Sinergia entre iniciativas,1.0,1.3,1.5,Factor de combinacion
efecto_total_incremental,21.1%,Calculo,Brecha × efecto multiplicador,10.3%,21.1%,27.4%,Impacto total proyectado
cac_promedio,485,Marketing Analytics,Costo de adquisicion actual,485,485,485,Promedio de 12 meses
costo_por_activacion_adicional,125,Calculo,Inversion / Clientes adicionales,2105,125,102,Costo por cliente nuevo activado
valor_por_dolar_invertido,69.2,Calculo,Ingresos anuales / Inversion,41.0,69.2,84.3,Retorno por cada USD invertido


// === ARCHIVO: documentacion/diagnostico.md ===
# Diagnóstico: Situación Actual de Activación de Clientes Nuevos

## Contexto del Negocio

La empresa opera como plataforma SaaS B2B con un modelo de freemium, donde los usuarios pueden 注册se gratuitamente pero necesitan activar su cuenta para acceder a funcionalidades premium. El problema identificado es una baja tasa de activación: de cada 100 clientes nuevos que se registran, solo 18 completan el proceso de activación en los primeros 30 días.

## Métricas Clave Actuales

| Métrica | Valor Actual | Valor Objetivo | Brecha |
|---------|--------------|----------------|--------|
| Tasa de activación D30 | 18% | 35% | -17 p.p. |
| Registros mensuales | 2.450 | 3.000 | -550 |
| Tiempo promedio de activación | 4.2 días | 2 días | +2.2 días |
| Tasa de completitud del onboarding | 42% | 70% | -28 p.p. |
| Engagement score (primeras 2 semanas) | 23/100 | 60/100 | -37 puntos |

## Fuentes de Datos

Los datos provienen de las siguientes fuentes consolidadas en el data warehouse:

1. **CRM (Salesforce)**: Registros de clientes, etapas del pipeline, datos demográficos de empresa.
2. **Plataforma analytics (Mixpanel)**: Eventos de usuario, funnels de conversión, cohortes de comportamiento.
3. **Sistema de soporte (Zendesk)**: Tickets abiertos durante onboarding, NPS post-onboarding.
4. **Base de datos transaccional (PostgreSQL)**: Uso real de funcionalidades, timeline de activación.
5. **Encuestas de churn (Typeform)**: Reasons para no activación, feedback cualitativo.

## Análisis del Funnel de Activación

### Etapa 1: Registro a Primera Acción
- **Registrados**: 2.450/mes
- **Primera acción en 7 días**: 1.715 (70%)
- **Conversión**: 70% (benchmark: 75%)
- **Gap**: 5 p.p. por debajo del benchmark

### Etapa 2: Primera Acción a Completar Perfil
- **Completan perfil**: 892 (36% del total)
- **Conversión**: 52%
- **Punto de fricción**: Formulario de 12 campos requerido
- **Feedback cualitativo**: "Tomó más tiempo del esperado", "No sabía para qué servían ciertos datos"

### Etapa 3: Perfil a Primer Uso de Feature Core
- **Usan feature core**: 441 (18% del total)
- **Conversión**: 49%
- **Punto de fricción**: Feature hidden en menú, sin guided tour
- **Feedback cualitativo**: "No encontré cómo empezar", "Necesitaba ayuda para el primer uso"

## Segmentación por Cohorte

| Segmento | % Registros | Tasa Activación | Observación |
|----------|-------------|-----------------|-------------|
| Pequeñas empresas (<10 empleados) | 45% | 12% | Menor adopción de herramientas B2B |
| Medianas (10-50) | 35% | 22% | Potencial de mejora |
| Grandes (>50) | 20% | 31% | Mejor adopción |

## Análisis de Correlación

Se realizó un análisis de correlación entre variables y la probabilidad de activación:

- **Tiempo de respuesta al primer email**: r = 0.67 (fuerte positiva)
- **Número de features exploradas en día 1**: r = 0.72 (fuerte positiva)
- **Completitud del perfil de empresa**: r = 0.58 (moderada positiva)
- **Tiempo hasta primera sesión**: r = -0.45 (moderada negativa)
- **Tickets de soporte en primera semana**: r = -0.23 (débil negativa)

## Problemas Identificados

1. **Fricción en onboarding**: Formulario extenso sin explicación de valor
2. **Falta de activación temprana**: No hay triggered emails en las primeras 24 horas
3. **Experiencia no personalizada**: Mismo flow para todos los segmentos
4. **Ausencia de social proof**: No se muestran casos de uso o testimonios durante onboarding
5. **Soporte reactivo**: No hay intervención proactiva para usuarios en riesgo

## Impacto Financiero

- Clientes no activados que churnan sin valor: ~1.607/mes
- Ingresos potenciales perdidos (LTV promedio $2.400): $3.856.800/año
- Costo de adquisición por cliente no recuperado: $180 promedio

## Supuestos del Diagnóstico

1. Los datos de Mixpanel tienen un delay de 24 horas, por lo que los números de este mes son estimates.
2. La segmentación por tamaño de empresa se basa en el campo "employees" del formulario de registro, con 23% de datos missing.
3. El benchmark de 75% para registro a primera acción proviene de平均值 de la industria SaaS B2B (fuente: OpenView 2024 SaaS Benchmarks).
4. El LTV de $2.400 se calculó con datos de los últimos 12 meses, con una retención promedio de 28 meses.

## Próximos Pasos

Este diagnóstico sustenta la construcción del árbol de métricas donde la tasa de activación D30 será la métrica objetivo, descompuesta en las palancas identificadas en este análisis.

// === ARCHIVO: documentacion/arbol-de-metricas.md ===
# Árbol de Métricas: Activación de Clientes Nuevos

## Métrica Raíz

**Tasa de Activación D30** = Porcentaje de clientes nuevos que completan al menos una acción de valor en los primeros 30 días después del registro.

- **Target**: 35% (actual: 18%)
- **Fuente de datos**: Mixpanel, evento "activation_completed"
- **Frecuencia de medición**: Diaria, reportado semanalmente

## Descomposición en Palancas de Primer Nivel

```
Tasa de Activación D30 (18% → 35%)
├── Velocidad de Tiempo al Valor
│   ├── Tiempo hasta primera acción significativa
│   └── Tiempo hasta primer uso de feature core
├── Profundidad de Engagement Inicial
│   ├── Número de features usadas en primera semana
│   └── Frecuencia de sesiones en primeras 2 semanas
├── Completitud del Onboarding
│   ├── Tasa de completitud del perfil de empresa
│   └── Tasa de completitud del setup técnico
└── Calidad de la Experiencia Inicial
    ├── NPS post-onboarding
    └── Tasa de resolución de bloqueos
```

## Palanca 1: Velocidad de Tiempo al Valor

### Definición
Mide cuán rápido el cliente nuevo puede experimentar el valor core del producto. A menor tiempo, mayor probabilidad de activación.

### Métricas Hijas

| Métrica | Actual | Target | Supuestos |
|---------|--------|--------|-----------|
| Tiempo hasta primera acción significativa | 2.1 días | 0.5 días | Trigger emails en <4 horas post-registro |
| Tiempo hasta primer uso de feature core | 4.2 días | 1.5 días | Guided tour obligatorio |
| Tiempo hasta primer "aha moment" | 3.8 días | 1.0 día | Feature highlight personalizado |

### Fuentes de Datos
- Mixpanel: eventos de tiempo hasta primer evento significativo
- PostgreSQL: timestamps de primer uso de cada feature
- Hipótesis: El benchmark de SaaS top performers indica 0.4 días promedio (fuente: Product Led Growth Collective)

### Iniciativas Vinculadas
- Implementar triggered email series en las primeras 24 horas
- Crear onboarding interactivo con feature highlight
- Personalizar primer dashboard basado en caso de uso declarado

## Palanca 2: Profundidad de Engagement Inicial

### Definición
Mide cuántas funcionalidades explora y con qué frecuencia el usuario en sus primeras semanas. La exploración profunda correlaciona con activación sostenida.

### Métricas Hijas

| Métrica | Actual | Target | Supuestos |
|---------|--------|--------|-----------|
| Features usadas en día 1 | 1.8 | 3.5 | Onboarding guiding + feature discovery |
| Features usadas en día 7 | 4.2 | 7.0 | Email nudges con casos de uso |
| Sesiones en primera semana | 2.3 | 5.0 | Notificaciones push + email digest |
| Días activos en primera quincena | 4.1 | 10.0 | Engagement campaigns |

### Fuentes de Datos
- Mixpanel: evento "feature_used" con propiedad "feature_name"
- PostgreSQL: conteo de sesiones por user_id
- Benchmark: Los productos con 7+ features en semana 1 tienen 3.2x mayor retención (fuente: Heap Product Benchmarks 2024)

### Iniciativas Vinculadas
- Diseñar feature discovery in-app
- Implementar email digest semanal personalizado
- Activar push notifications para re-engagement

## Palanca 3: Completitud del Onboarding

### Definición
Mide cuántos de los pasos recomendados de onboarding completa el usuario. Un onboarding completo establece las bases para uso sostenido.

### Métricas Hijas

| Métrica | Actual | Target | Supuestos |
|---------|--------|--------|-----------|
| Tasa de completitud de perfil | 52% | 85% | Reducir campos + explicar valor |
| Tasa de completitud de setup técnico | 38% | 70% | Documentación mejorada + soporte in-app |
| Tasa de completitud de onboarding flow | 42% | 75% | Progress indicator + incentivos |
| Paso más abandonado | Paso 3 (configuración) | N/A | Fricción en integración API |

### Fuentes de Datos
- Mixpanel: funnel de onboarding con drop-off por paso
- Salesforce: completitud de campos de cuenta
- Encuesta: "¿Qué te detuvo en el onboarding?" (Typeform)

### Iniciativas Vinculadas
- Rediseñar formulario de registro (12 → 5 campos obligatorios)
- Crear wizard de setup técnico con validación en tiempo real
- Implementar progress bar con rewards por completitud

## Palanca 4: Calidad de la Experiencia Inicial

### Definición
Mide la satisfacción y resolución de problemas durante el onboarding. Una experiencia positiva reduce churn temprano.

### Métricas Hijas

| Métrica | Actual | Target | Supuestos |
|---------|--------|--------|-----------|
| NPS post-onboarding | 32 | 55 | Mejora en UX + soporte proactivo |
| Tasa de resolución de bloqueos | 45% | 80% | Chat in-app + knowledge base |
| Tiempo de resolución de primer ticket | 18 horas | 4 horas | SLA para tickets de onboarding |
| Tasa de usuarios que piden ayuda y activan | 28% | 50% | Intervención proactiva |

### Fuentes de Datos
- Typeform: NPS survey envía en D7
- Zendesk: tiempo hasta primera respuesta, satisfacción del ticket
- Intercom: chats iniciados durante onboarding

### Iniciativas Vinculadas
- Implementar chat in-app con SLA de 2 minutos
- Crear knowledge base contextual por paso de onboarding
- Activar intervención proactiva para usuarios stuck >48 horas

## Matriz de Impacto de Palancas

| Palanca | Impacto en Activación | Facilidad de Implementación | Dependencias |
|---------|----------------------|----------------------------|--------------|
| Velocidad de Tiempo al Valor | Alta (estudios muestran 0.7 correlación) | Media | Marketing automation |
| Profundidad de Engagement | Alta (0.72 correlación) | Alta | Product analytics setup |
| Completitud del Onboarding | Media-Alta (0.58 correlación) | Baja | UX research |
| Calidad de Experiencia | Media (0.45 correlación) | Media | Customer success |

## Supuestos del Árbol de Métricas

1. Las correlaciones mencionadas provienen del análisis de correlación del diagnóstico (r de Pearson).
2. Los benchmarks son de industria SaaS B2B promedio (OpenView, Heap, Product Led Growth Collective).
3. Los targets son agresivos pero alcanzables en 6 meses con las iniciativas propuestas.
4. La suma de las mejoras en palancas no es lineal: el efecto compuesto se estima en 1.3x por sinergias.

## Validación del Árbol

Para validar que el árbol está bien construido, cada métrica hija debe responder a:
- ¿Tenemos la fuente de datos para medirla?
- ¿Podemos influir en ella con iniciativas concretas?
- ¿El cambio en la métrica hija mueve la métrica padre?

Todas las métricas cumplen estos tres criterios.

// === ARCHIVO: documentacion/plan-de-accion.md ===
# Plan de Acción: Iniciativas para Aumentar la Activación de Clientes Nuevos

## Priorización General

Las iniciativas se priorizaron usando una matriz de impacto (1-5) vs. esfuerzo (1-5), donde:
- **Impacto 5**: Mueve la métrica objetivo >5 p.p.
- **Impacto 4**: Mueve la métrica 3-5 p.p.
- **Impacto 3**: Mueve la métrica 1-3 p.p.
- **Esfuerzo 5**: Requiere >3 meses de desarrollo
- **Esfuerzo 4**: Requiere 2-3 meses
- **Esfuerzo 3**: Requiere 1-2 meses
- **Esfuerzo 2**: Requiere 2-4 semanas
- **Esfuerzo 1**: Requiere <2 semanas

## Iniciativas Priorizadas

### Iniciativa 1: Triggered Email Series

| Atributo | Detalle |
|----------|---------|
| **Prioridad** | 1 (Impacto 5, Esfuerzo 2) |
| **Dueño** | Marketing (María González) |
| **Plazo** | 6 semanas |
| **Criterio de éxito** | Tasa de apertura >40%, tasa de clic >8%, reducción de tiempo hasta primera acción de 2.1 a 0.8 días |
| **Presupuesto** | $8.000 (herramienta de email automation) |
| **Dependencias** | Integración Mixpanel → Klaviyo |

**Descripción**: Serie de 5 emails automatizados activados por comportamiento del usuario en las primeras 72 horas: (1) Bienvenida + valor core, (2) Guía de primer paso, (3) Caso de uso relevante por segmento, (4) Social proof/testimonial, (5) Última llamada a acción.

**Métricas a seguir**:
- Email open rate por email
- Click-through rate por email
- Tiempo hasta primera acción post-email
- Conversión a activación por cohort

---

### Iniciativa 2: Rediseño del Formulario de Registro

| Atributo | Detalle |
|----------|---------|
| **Prioridad** | 2 (Impacto 5, Esfuerzo 1) |
| **Dueño** | Producto (Carlos Ruiz) |
| **Plazo** | 3 semanas |
| **Criterio de éxito** | Reducción de campos obligatorios de 12 a 5, increase en tasa de completitud de perfil de 52% a 75%, incremento en tasa de activación de 18% a 22% |
| **Presupuesto** | $0 (trabajo interno) |
| **Dependencias** | UX research, Salesforce (actualización de campos)

**Descripción**: Rediseño del formulario de registro con estrategia de campos progresivos: solo email y contraseña requeridos inicialmente, resto del perfil solicitado contextualmente durante onboarding. Se elimina la fricción inicial manteniendo la captura de datos necesaria para personalización.

**Métricas a seguir**:
- Tasa de completitud del registro
- Tiempo de completion del registro
- Tasa de completitud de perfil a D7
- Conversión registro → activación

---

### Iniciativa 3: Onboarding Interactivo con Guided Tour

| Atributo | Detalle |
|----------|---------|
| **Prioridad** | 3 (Impacto 4, Esfuerzo 3) |
| **Dueño** | Producto (Ana Martínez) |
| **Plazo** | 10 semanas |
| **Criterio de éxito** | Reducción de tiempo hasta primer uso de feature core de 4.2 a 2.0 días, increase en features usadas en día 1 de 1.8 a 3.0 |
| **Presupuesto** | $15.000 (herramienta de onboarding) |
| **Dependencias** | Product analytics, Engineering capacity

**Descripción**: Implementación de guided tour interactivo que acompaña al usuario en sus primeras interacciones con el producto. El tour se adapta al caso de uso declarado y al segmento del usuario, highlighteando las features más relevantes para su contexto.

**Métricas a seguir**:
- Tasa de completitud del guided tour
- Tiempo hasta primer uso de feature core
- Features usadas en día 1 y día 7
- Correlación tour completion → activación

---

### Iniciativa 4: Chat In-App con Soporte Proactivo

| Atributo | Detalle |
|----------|---------|
| **Prioridad** | 4 (Impacto 4, Esfuerzo 2) |
| **Dueño** | Customer Success (Laura Fernández) |
| **Plazo** | 5 semanas |
| **Criterio de éxito** | Tasa de resolución de bloqueos de 45% a 70%, tiempo de resolución <4 horas, incremento en activación de usuarios que contactan soporte de 28% a 45% |
| **Presupuesto** | $12.000/año (Intercom) |
| **Dependencias** | Integración con Zendesk, training del equipo

**Descripción**: Implementación de chat in-app con las siguientes características: (1) Bot conversacional para preguntas frecuentes, (2) Escalamiento a agente humano con SLA de 2 minutos, (3) Triggers proactivos cuando el usuario está >48 horas sin actividad, (4) Knowledge base contextual por paso de onboarding.

**Métricas a seguir**:
- Tasa de resolución en primer contacto
- Tiempo promedio de primera respuesta
- Satisfacción del usuario (CSAT)
- Conversión a activación de usuarios que usaron chat

---

### Iniciativa 5: Personalización del Dashboard Inicial

| Atributo | Detalle |
|----------|---------|
| **Prioridad** | 5 (Impacto 3, Esfuerzo 3) |
| **Dueño** | Producto (Carlos Ruiz) |
| **Plazo** | 8 semanas |
| **Criterio de éxito** | Increase en engagement score de 23 a 45, reducción de tiempo hasta primer "aha moment" de 3.8 a 2.0 días |
| **Presupuesto** | $0 (trabajo interno) |
| **Dependencias** | Datos de segmento en Salesforce, Engineering

**Descripción**: El dashboard inicial se personaliza según el caso de uso declarado en el registro y el segmento de empresa. Se muestran métricas relevantes para su industria, templates pre-configurados y ejemplos de contenido que resuenan con su contexto.

**Métricas a seguir**:
- Engagement score por segmento
- Tiempo hasta primer "aha moment"
- Tasa de retorno al dashboard
- NPS por tipo de dashboard

---

### Iniciativa 6: Feature Discovery In-App

| Atributo | Detalle |
|----------|---------|
| **Prioridad** | 6 (Impacto 3, Esfuerzo 2) |
| **Dueño** | Producto (Ana Martínez) |
| **Plazo** | 4 semanas |
| **Criterio de éxito** | Increase en features usadas en día 7 de 4.2 a 6.0, reducción de features abandonadas sin uso |
| **Presupuesto** | $5.000 (herramienta de feature flags) |
| **Dependencias** | Product analytics, Feature flag system

**Descripción**: Sistema de tooltips y cards de descubrimiento que aparecen contextualmente cuando el usuario ha usado una feature por unos días, sugiriendo features relacionadas que complementan su flujo de trabajo actual.

**Métricas a seguir**:
- Tasa de click en feature suggestions
- Features usadas antes/después de suggestion
- Incremento en feature breadth
- Correlación discovery → activación

---

### Iniciativa 7: Email Digest Personalizado Semanal

| Atributo | Detalle |
|----------|---------|
| **Prioridad** | 7 (Impacto 2, Esfuerzo 2) |
| **Dueño** | Marketing (María González) |
| **Plazo** | 4 semanas |
| **Criterio de éxito** | Increase en sesiones en primera semana de 2.3 a 3.5, open rate del digest >35% |
| **Presupuesto** | $0 (usando Klaviyo existente) |
| **Dependencias** | Datos de comportamiento de Mixpanel

**Descripción**: Email semanal personalizado que resume la actividad del usuario en la plataforma, destaca features no usadas que podrían ser relevantes, y muestra tips para maximizar el valor del producto.

**Métricas a seguir**:
- Open rate y click-through rate
- Incremento en sesiones post-digest
- Features exploradas post-digest

---

## Roadmap Consolidado

```
Mes 1-2:
├── Iniciativa 2: Rediseño de registro (3 sem)
├── Iniciativa 1: Triggered emails (6 sem - inicio paralelo)
└── Iniciativa 4: Chat in-app (5 sem - inicio paralelo)

Mes 2-3:
├── Iniciativa 6: Feature discovery (4 sem)
├── Iniciativa 7: Email digest (4 sem)
└── Iniciativa 3: Onboarding interactivo (10 sem - inicio)

Mes 3-4:
├── Iniciativa 3: Onboarding interactivo (continuación)
└── Iniciativa 5: Dashboard personalizado (8 sem - inicio)

Mes 4-5:
└── Iniciativa 5: Dashboard personalizado (continuación)
```

## Criterios de Éxito del Programa

| Métrica | Baseline | Target D3 | Target D6 |
|---------|----------|-----------|-----------|
| Tasa de activación D30 | 18% | 25% | 35% |
| Tiempo hasta primera acción | 2.1 días | 1.2 días | 0.5 días |
| Features usadas día 7 | 4.2 | 5.5 | 7.0 |
| NPS post-onboarding | 32 | 42 | 55 |

## Gestión de Riesgos

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Retraso en integración Mixpanel-Klaviyo | Media | Alto | Iniciar integración en semana 1, tener fallback manual |
| Resistencia al cambio en formulario de registro | Alta | Medio | A/B test gradual, mantener datos existentes |
| Capacidad de engineering limitada | Alta | Alto | Priorizar iniciativas de bajo esfuerzo, considerar contractor |
| Caída en métricas durante transición | Media | Alto | Rollout gradual, métricas de rollback definidas |

## Recursos Asignados

- **Producto**: 2 FTEs (Carlos, Ana)
- **Marketing**: 1 FTE (María)
- **Customer Success**: 0.5 FTE (Laura)
- **Engineering**: 2 FTEs (backend), 1 FTE (frontend)
- **Presupuesto total**: $40.000 + $12.000/año recurrentes


// === ARCHIVO: documentacion/recomendacion.md ===
# Recomendación Estratégica: Iniciativas para Aumentar la Activación de Clientes Nuevos

## Resumen Ejecutivo

Después de analizar el árbol de métricas, las hipótesis identificadas y el modelo cuantitativo, la recomendación prioritaria es implementar un programa de onboarding guiado con personalización basada en segmento de cliente. Esta recomendación se fundamenta en el análisis de impacto estimado, esfuerzo requerido y validabilidad de los supuestos con datos disponibles.

## Recomendación Principal: Programa de Onboarding Personalizado

### Descripción de la Iniciativa

Implementar un flujo de onboarding en 3 etapas que guíe al cliente nuevo a través de la configuración inicial del producto, con contenido y timing personalizado según el segmento al que pertenece el cliente (B2B, B2C, Enterprise).

### Justificación Basada en Datos

**Impacto estimado en activación:**
- Incremento proyectado en tasa de activación del 23% al 34% (11 puntos porcentuales)
- Corresponde a un incremento en clientes activos de 2.300 a 3.400 mensuales
- Revenue adicional proyectado: $85.000-$120.000 mensuales

**Supuestos validados:**
- La tasa de activación actual del 23% se extrajo del sistema CRM (Salesforce) con datos de los últimos 6 meses
- El benchmark de la industria para onboarding efectivo indica mejoras de 8-15 puntos porcentuales (fuente: Industry Report 2024, SaaS Metrics Standard)
- El segmento de clientes B2B tiene la menor tasa de activación actual (18%) pero el mayor valor de lifetime, lo que maximiza el ROI de la iniciativa

**Criterios de éxito medibles:**
- Tasa de completación del onboarding > 60% en los primeros 30 días
- Activación medida como primer uso del feature core dentro de los primeros 7 días
- Net Promoter Score del onboarding > 40

## Alternativas Descartadas

### Alternativa 1: Campaña de Email Marketing Masivo

**Descripción:** Envío de secuencias de email automatizadas a todos los clientes nuevos sin segmentación.

**Razón del descarte:**
- Impacto estimado menor: solo 4-6 puntos porcentuales de mejora vs. 11 puntos del onboarding personalizado
- La tasa de apertura de emails actual es del 18%, significativamente por debajo del benchmark de 25%
- No aprovecha la oportunidad de segmentación que los datos de CRM permiten
- ROI proyectado: $25.000-$35.000 mensuales vs. $85.000-$120.000 del onboarding personalizado

### Alternativa 2: Descuentos en el Primer Mes

**Descripción:** Ofrecer un descuento del 30% en la primera factura para clientes que activen dentro de los primeros 7 días.

**Razón del descarte:**
- Impacto en activación real es marginal (2-3 puntos porcentuales según datos históricos de promociones)
- Reduce el revenue del primer mes en un 30%, compensando cualquier ganancia por mayor activación
- Puede generar efecto de anclaje negativo en la percepción de valor del producto
-ROI proyectado negativo: -$15.000-$5.000 mensuales

### Alternativa 3: Chat de Soporte 24/7 para Clientes Nuevos

**Descripción:** Implementar un canal de soporte prioritario exclusivo para clientes en sus primeros 30 días.

**Razón del descarte:**
- Requiere inversión significativa en personal (estimado: 3 agentes adicionales, $15.000/mes)
- El análisis de tickets de soporte muestra que solo el 12% de los clientes nuevos genera tickets en el primer mes
- El impacto en activación sería indirecto y difícil de atribuir
-ROI proyectado: $10.000-$20.000 mensuales, significativamente menor que el onboarding personalizado

### Alternativa 4: Gamificación del Producto

**Descripción:** Añadir elementos de gamificación (badges, niveles, leaderboards) para aumentar el engagement inicial.

**Razón del descarte:**
- El esfuerzo de implementación es alto (estimado: 3-4 meses de desarrollo)
- El segmento Enterprise (35% de los clientes nuevos) no responde positivamente a elementos de gamificación según feedback cualitativo
- Puede generar adopción de features no-core, diluyendo el foco en la activación del feature principal
-ROI proyectado: $30.000-$45.000 mensuales con alta incertidumbre

## Análisis de Sensibilidad

El modelo cuantitativo soporta los siguientes escenarios:

| Escenario | Tasa de Activación | Impacto Mensual | Probabilidad |
|-----------|-------------------|-----------------|--------------|
| Conservador | 28% | $65.000 | 40% |
| Base | 34% | $102.000 | 45% |
| Optimista | 40% | $145.000 | 15% |

**Factores de riesgo identificados:**
- Resistencia al cambio de clientes existentes (mitigable con comunicación proactiva)
- Retraso en desarrollo por dependencias técnicas (mitigable con sprint dedicado)
- Saturación del equipo de producto (mitigable con recursos adicionales)

## Próximos Pasos Recomendados

1. **Inmediato (Semana 1-2):** Validar supuestos con el equipo de producto y tecnología
2. **Corto plazo (Semana 3-6):** Diseñar prototipos del flujo de onboarding para los 3 segmentos
3. **Medio plazo (Semana 7-12):** Implementar MVP del segmento B2B (mayor impacto potencial)
4. **Largo plazo (Semana 13-20):** Escalar a segmentos B2C y Enterprise

## Stakeholders Clave

- **Patrocinador Ejecutivo:** VP de Producto
- **Dueño del Proyecto:** Director de Growth
- **Equipo de Implementación:** Equipo de Producto + Ingeniería
- **Métricas de seguimiento:** Equipo de Analytics

---
*Documento generado en el contexto del análisis de activación de clientes nuevos. Los datos provienen de CRM, sistema de analytics y benchmarks de industria.*

// === ARCHIVO: documentacion/matriz-priorizacion.md ===
# Matriz de Priorización de Iniciativas

## Marco de Priorización: Impacto vs. Esfuerzo

La siguiente matriz utiliza una escala de 1 a 5 para evaluar cada iniciativa según dos dimensiones:

- **Impacto (I):** Beneficio potencial medido en incremento de la tasa de activación de clientes nuevos
- **Esfuerzo (E):** Recursos necesarios para implementar la iniciativa (tiempo, costo, complejidad técnica)

**Fórmula de Prioridad:** `Puntuación = Impacto × (6 - Esfuerzo)`

Esta fórmula favorece iniciativas de alto impacto y bajo esfuerzo, penalizando proporcionalmente las que requieren mayor inversión de recursos.

## Matriz Visual

```
                    ESFUERZO
      1       2       3       4       5
    ┌───────┬───────┬───────┬───────┬───────┐
 5  │  ★5   │  8    │ 11    │ 12    │  5    │ I
    │       │       │       │       │       │ M
 4  │  4    │  ★8   │ 12    │ 12    │  8    │ P
    │       │       │       │       │       │ A
 3  │  3    │  6    │  ★9   │  9    │  6    │ C
    │       │       │       │       │       │ T
 2  │  2    │  4    │  6    │  ★8   │  4    │ O
    │       │       │       │       │       │
 1  │  1    │  2    │  3    │  4    │  ★5   │
    └───────┴───────┴───────┴───────┴───────┘
```

**Leyenda:**
- ★ = Iniciativas priorizadas (cuadrante óptimo: alto impacto, bajo esfuerzo)
- Las celdas sombreadas en gris claro representan iniciativas de segunda prioridad
- Las celdas en blanco son iniciativas de menor prioridad o alto riesgo

## Detalle de Iniciativas Evaluadas

### Cuadrante Óptimo: Alto Impacto / Bajo Esfuerzo (Prioridad Alta)

| # | Iniciativa | Impacto | Esfuerzo | Puntuación | Estado |
|---|------------|---------|----------|------------|--------|
| 1 | Onboarding personalizado por segmento | 5 | 2 | 20 | ★ Prioritaria |
| 2 | Optimización del email de bienvenida | 4 | 1 | 20 | ★ Alta |
| 3 | Segmentación de clientes nuevos en CRM | 4 | 2 | 16 | ★ Alta |
| 4 | Dashboard de activación para CSM | 3 | 1 | 15 | ★ Alta |

### Cuadrante de Desarrollo: Alto Impacto / Medio Esfuerzo

| # | Iniciativa | Impacto | Esfuerzo | Puntuación | Estado |
|---|------------|---------|----------|------------|--------|
| 5 | Programa de onboarding guiado | 5 | 3 | 15 | Segunda |
| 6 | Integración con herramientas de analytics | 4 | 3 | 12 | Segunda |
| 7 | Automatización de follow-up | 4 | 3 | 12 | Segunda |
| 8 | Personalización de contenido in-app | 4 | 3 | 12 | Segunda |

### Cuadrante de Evaluación: Impacto Medio / Bajo Esfuerzo

| # | Iniciativa | Impacto | Esfuerzo | Puntuación | Estado |
|---|------------|---------|----------|------------|--------|
| 9 | Mejora de documentación de producto | 3 | 2 | 12 | Evaluación |
| 10 | Checklist de primeros 7 días | 3 | 2 | 12 | Evaluación |
| 11 | Videos tutoriales cortos | 3 | 2 | 12 | Evaluación |

### Cuadrante de Optimización: Impacto Medio / Medio Esfuerzo

| # | Iniciativa | Impacto | Esfuerzo | Puntuación | Estado |
|---|------------|---------|----------|------------|--------|
| 12 | Chat de soporte para nuevos clientes | 3 | 3 | 9 | Optimizar |
| 13 | Webinars de capacitación | 3 | 3 | 9 | Optimizar |
| 14 | Comunidad de usuarios | 3 | 4 | 6 | Optimizar |

### Cuadrante de Bajo Prioridad: Bajo Impacto o Alto Esfuerzo

| # | Iniciativa | Impacto | Esfuerzo | Puntuación | Estado |
|---|------------|---------|----------|------------|--------|
| 15 | Gamificación del producto | 4 | 4 | 8 | Baja |
| 16 | Descuentos por activación temprana | 2 | 3 | 6 | Baja |
| 17 | Programa de referidos | 3 | 5 | 3 | Baja |
| 18 | App móvil nativa | 4 | 5 | 4 | Baja |

## Criterios de Evaluación Detallados

### Escala de Impacto (1-5)

| Nivel | Descripción | Métrica de Referencia |
|-------|-------------|----------------------|
| 1 | Impacto marginal | < 2pp de mejora en activación |
| 2 | Impacto bajo | 2-4pp de mejora en activación |
| 3 | Impacto moderado | 4-7pp de mejora en activación |
| 4 | Impacto alto | 7-10pp de mejora en activación |
| 5 | Impacto muy alto | > 10pp de mejora en activación |

### Escala de Esfuerzo (1-5)

| Nivel | Descripción | Recursos Estimados |
|-------|-------------|-------------------|
| 1 | Esfuerzo mínimo | < 1 sprint, < $5K |
| 2 | Esfuerzo bajo | 1-2 sprints, $5K-$15K |
| 3 | Esfuerzo medio | 2-3 sprints, $15K-$30K |
| 4 | Esfuerzo alto | 3-4 sprints, $30K-$50K |
| 5 | Esfuerzo muy alto | > 4 sprints, > $50K |

## Roadmap Sugerido

### Inmediato (0-2 meses)
- Implementar optimización del email de bienvenida (I=4, E=1)
- Configurar segmentación en CRM (I=4, E=2)
- Crear dashboard de activación (I=3, E=1)

### Corto plazo (2-4 meses)
- Desarrollar MVP de onboarding personalizado (I=5, E=2)
- Implementar automatización de follow-up (I=4, E=3)
- Crear checklist de primeros 7 días (I=3, E=2)

### Medio plazo (4-8 meses)
- Programa completo de onboarding guiado (I=5, E=3)
- Integración con herramientas de analytics (I=4, E=3)
- Personalización de contenido in-app (I=4, E=3)

### Largo plazo (8+ meses)
- Evaluar gamificación (I=4, E=4)
- Considerar comunidad de usuarios (I=3, E=4)
- Evaluar app móvil (I=4, E=5)

## Factores de Ajuste Dinámico

La priorización debe revisarse mensualmente considerando:

1. **Cambios en datos de activación:** Si la tasa base cambia significativamente, recalcular el impacto esperado
2. **Disponibilidad de recursos:** Ajustar el esfuerzo estimado según capacidad del equipo
3. **Feedback de clientes:** Incorporar insights cualitativos que puedan cambiar la percepción de impacto
4. **Competencia:** Monitorear iniciativas de competidores que puedan obsoletizar prioridades
5. **Dependencias técnicas:** Actualizar esfuerzo si surgen bloqueos técnicos

---
*Matriz actualizada en función del análisis de árbol de métricas y modelo cuantitativo. Fecha de última actualización: [Insertar fecha].*


// === ARCHIVO: modelos/hipotesis.csv ===
id_hipotesis,hipotesis,palanca_principal,impacto_estimado,esfuerzo_estimado,forma_validacion,supuestos_clave,estado_validacion
H1,Reducir el tiempo de onboarding de 7 a 3 días aumenta la tasa de activación en un 25%,Onboarding流畅,4,3,A/B test con 500 usuarios nuevos durante 4 semanas,Tasa actual de activación es 35%; el tiempo de onboarding correlaciona negativamente con activación (r=-0.72),pendiente
H2,Implementar emails automatizados de activación en D+1, D+3 y D+7 incrementa la activación un 15%,Comunicación proactiva,3,2,Análisis de cohortes comparando usuarios con/sin emails en 8 semanas,Open rate esperado >40%; la secuencia actual tiene CTR de 2.1%,validada
H3,Ofrecer una sesión de onboarding personalizada con un customer success manager incrementa la activación en un 30% para el segmento enterprise,Segmentación + CSM,5,4,Test con 50 clientes enterprise en Q1; medir activación a 30 días,El segmento enterprise representa 15% de nuevos clientes; ticket promedio $50k/año,pendiente
H4,Simplificar el primer flujo de uso a 3 clicks reduce la fricción y aumenta la activación un 20%,UX/UI,4,3,Heatmaps y funnel analysis pre/post cambio en 2 semanas,El flujo actual tiene 7 pasos; usuarios abandonan en paso 4 (60% dropoff),pendiente
H5,Crear un centro de recursos (academy) con tutorials interactivos incrementa la activación un 12%,Educación del usuario,3,2,Métricas de usage de academy vs activación en 3 meses,50% de usuarios acceden a documentación; completion rate de tutorials es 25%,analizando
H6,Implementar gamificación (badges, progress bars) en el primer uso aumenta la activación un 18%,Engagement,3,3,A/B test con gamificación vs control durante 6 semanas,Users younger de 35 años responden mejor a gamificación (estudios muestran +22% engagement),pendiente
H7,Enviar notificaciones push de recordatorio en D+2 y D+5 aumenta la activación un 10%,Notificaciones,2,1,Análisis de push open rate y conversión en 4 semanas,Opt-in rate actual de push es 60%; notification fatigue no supera el 5%,validada
H8,Ofrecer试用期 extendido de 30 días (vs 14 días actual) para usuarios que no se activan en los primeros 7 días incrementa la activación un 8%,Políticas de试用期,2,2,Test con 200 usuarios en 6 semanas,Usuarios que no se activan en D+7 tienen 40% probabilidad de activación si se extiende试用期,pendiente
H9,Crear comunidad de usuarios (Slack/Discord) con canal de onboarding incrementa la activación un 14%,Comunidad,3,3,Métricas de join rate a comunidad y correlación con activación en 6 meses,Comunidad activa tiene 2.3x más probabilidad de activación,analizando
H10,Personalizar la experiencia de onboarding según el tamaño de empresa y vertical aumenta la activación un 22%,Segmentación + Personalización,5,5,Test A/B con segmentación vs one-size-fits-all en 8 semanas,Existen 4 segmentos principales con diferentes pain points; el mensaje relevante mejora conversión 35%,pendiente

// === ARCHIVO: modelos/modelo.csv ===
variable,descripcion,valor_base,fuente,rango_min,rango_max,formula_relacion,notas
MAU_nuevo,Clientes nuevos que se activan en los primeros 30 días,350,Data Warehouse - tabla activations,200,500,,Meta principal del modelo
TC_tasa_conversion,Tasa de conversión de lead a cliente nuevo,0.12,CRM - funnel report,0.08,0.18,,Base del funnel
TA_tasa_act,Tasa de activación (cliente nuevo que completa el flujo de onboarding),0.35,Data Warehouse - tabla activations,0.25,0.50,MAU_nuevo = TC_tasa_conversion * LEADS * TA_tasa_act,Métrica objetivo a optimizar
LEADS,Leads generados mensuales,2500,Marketing - plataforma de ads,1500,4000,,Input del funnel
TP_onboarding,Tiempo promedio de onboarding (días),7,Product Analytics - user journey,3,14,TA_tasa_act = 0.62 - 0.04 * TP_onboarding,Correlación negativa validada con r=-0.72
TC_email,Tasa de apertura de emails de activación,0.42,Email platform,0.30,0.55,,Secuencia D+1, D+3, D+7
TC_push,Tasa de apertura de push notifications,0.55,Mobile SDK,0.40,0.70,,Notificaciones en D+2, D+5
Tasa_engagement,Tasa de engagement con el producto (acciones/semana),3.2,Product Analytics,1.5,6.0,TA_tasa_act = 0.15 + 0.08 * Tasa_engagement,Proxy fuerte de activación
NR_NPS,NPS de usuarios nuevos (encuesta D+30),42,Customer Success,25,65,,Correlación con activación r=0.58
TC_csmpersonalizado,Tasa de activación con CSM personalizado (segmento Enterprise),0.65,CS team - tracking,0.50,0.80,,Para clientes con ARR>$50k
Tasa_soporte,Tasa de resolución en primer contacto para nuevos usuarios,0.78,Support desk,0.60,0.90,,Tickets relacionados con onboarding
TC_academy,Tasa de completación de tutorials de academy,0.25, LMS interno,0.15,0.40,,Completion del onboarding path
Tasa_gamificacion,Tasa de activación con gamificación,0.41, A/B test results,0.35,0.50,,Para segmento <35 años

ESCENARIO,parametro_cambiado,nuevo_valor,impacto_activacion,impacto_mau_nuevo,delta_mensual,probabilidad,notas
Base,—,—,0.350,350,—,1.00,Escenario actual sin cambios
Optimista_email,TC_email,0.55,0.388,388,+38,0.25,Secuencia de emails optimizada con contenido personalizado
Conservador_email,TC_email,0.30,0.359,359,+9,0.30,Decreased open rates por saturación
Optimista_onboarding,TP_onboarding,3,0.470,470,+120,0.20,Onboarding reducido a 3 días con nueva UX
Conservador_onboarding,TP_onboarding,14,0.220,220,-130,0.10,Si el onboarding se complica por falta de recursos
Combinado_email_onboarding,TC_email+TP_onboarding,0.55 / 3,0.494,494,+144,0.15,Mejora en ambos factores simultáneamente
Enterprise_csm,TC_csmpersonalizado,0.65,0.365,365,+15,0.20,CSM solo para enterprise (15% del total)
Gamificacion_jovenes,Tasa_gamificacion,0.41,0.362,362,+12,0.25,Gamificación para segmento joven (40% de usuarios)
Peor_caso,TP_onboarding+TC_email,14 / 0.30,0.182,182,-168,0.05,Escenario de riesgo: onboarding lento + emails ignorados
Mejor_caso,TP_onboarding+TC_email,3 / 0.55,0.530,530,+180,0.10,Escenario ideal: onboarding rápido + emails efectivos

SENSIBILIDAD,variable,sensibilidad_elasticidad,impacto_1%_aumento,comentario
Elasticidad_TP_onboarding,TP_onboarding,-0.058,-0.58%,Por cada día adicional de onboarding, la activación baja 0.58%
Elasticidad_TC_email,TC_email,0.032,+0.32%,Por cada 1% de aumento en open rate, activación sube 0.32%
Elasticidad_Tasa_engagement,Tasa_engagement,0.125,+1.25%,Por cada acción adicional por semana, activación sube 1.25%
Elasticidad_NPS,NR_NPS,0.004,+0.04%,Por cada punto de NPS, activación sube 0.04% (débil directo, vía satisfacción)
Elasticidad_TC_csmpersonalizado,TC_csmpersonalizado,0.003,+0.03%,Impacto directo pero solo para 15% de usuarios enterprise

SUPuesto,descripcion,valor,fuente,fecha_actualizacion,confianza,notas
S1,Tasa de activación baseline 35%,0.35,Data Warehouse - últimos 6 meses,2025-01-15,alta,Medida como usuarios que completan onboarding en 30 días
S2,Correlación tiempo-onboarding y activación,r=-0.72,Análisis de regresión histórico,2025-01-10,alta,Dataset de 5000 usuarios con comportamiento de onboarding
S3,Distribución de segmentos: Enterprise 15%, SMB 60%, Startup 25%,—,CRM + Data Warehouse,2025-01-12,alta,Basado en ARR y tamaño de empresa
S4,Email sequence actual tiene CTR de 2.1%,0.021,Email platform - último trimestre,2025-01-14,media,CTR bajo indica necesidad de optimización
S5,Usuarios que no se activan en D+7 tienen 40% chance si se extiende试用期,0.40,Estudio de cohorts históricas,2025-01-08,media,Análisis de usuarios que reactivaron con extensión
S6,Presupuesto disponible para iniciativas,Q2 2025: $120k,Finance,2025-01-01,alta,Incluye herramientas, personal y tecnología
S7,Equipo disponible: 2 PMs, 1 UX, 3 devs, 1 data analyst,—,HR - resource planning,2025-01-05,alta,Capacidad de ejecución en el quarter
S8,Timeline de implementación: 8 semanas para iniciativas maiores,8,Project plan,2025-01-02,media,Incluye desarrollo, testing y rollout
S9,Tasa de conversión lead→cliente actual,0.12,CRM,2025-01-15,alta,No es foco de este análisis pero es input del funnel
S10,Usuarios con edad <35 años representan 40% de la base,0.40,User analytics,2025-01-11,media,Dato relevante para iniciativas de gamificación

```
