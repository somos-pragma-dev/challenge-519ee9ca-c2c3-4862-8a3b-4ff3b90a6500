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
- Título: Diseño y Priorización de Árbol de Métricas
- Tiempo estimado: 8 horas

### Fases (trabajo del HUMANO — PROHIBIDO completarlas)
No implementes estos entregables. Dejalos como hueco pedagógico. El asistente solo materializa el proyecto arrancable para que el participante pueda trabajar.
- Fase 1: Definición de la Métrica Objetivo — objetivo: Clarificar y definir la métrica objetivo 'activación de clientes nuevos' en términos del negocio. — entregable (NO resolver): Descripción clara y detallada de la métrica objetivo 'activación de clientes nuevos'.
- Fase 2: Descomposición de la Métrica en Palancas Accionables — objetivo: Descomponer la métrica objetivo en diferentes iniciativas o palancas accionables. — entregable (NO resolver): Árbol de métricas que descompone la métrica objetivo en diferentes iniciativas o palancas accionables.
- Fase 3: Priorización de Iniciativas — objetivo: Priorizar las iniciativas identificadas basándote en su impacto y el esfuerzo requerido para implementarlas. — entregable (NO resolver): Lista de iniciativas priorizadas con supuestos explícitos sobre su impacto y el esfuerzo requerido para implementarlas.

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

// === ARCHIVO: datos/hipotesis.csv ===
id_iniciativa,nombre_iniciativa,palanca_principal,impacto_estimado,esfuerzo_estimado,justificacion,forma_validacion,metricas_asociadas,responsable,plazo_meses
H1,Onboarding guiado de 7 días,Experiencia de usuario,Alto,Medio,"El onboarding estructurado reduce el tiempo hasta la primera acción exitosa. Datos de benchmarks del sector muestran que usuarios con onboarding guiado tienen 40% mayor probabilidad de activación en los primeros 7 días. El esfuerzo es medio porque requiere diseño de flujos y contenido, pero no infraestructura compleja.","A/B test: grupo con onboarding vs grupo control durante 30 días. Métrica: % de usuarios que completan onboarding y realizan acción valuable en D7.","Tasa de activación D7,Tiempo hasta primera acción,Completación de onboarding",Producto,2
H2,Programa de incentivos por primera acción,Economía del usuario,Alto,Alto,"Los incentivos (descuentos, créditos, beneficios) aceleran la primera transacción. Estudios de economía conductual muestran que el efecto de ‘anclaje’ con incentivo inicial aumenta la activación en 25-35%. El esfuerzo es alto porque requiere integración con sistemas de rewards y presupuesto连续.","Piloto con segmento de usuarios nuevos (N=5000). Grupo con incentivo de $10 vs control sin incentivo. Medir tasa de primera transacción en D14.","Tasa de primera transacción,Valor lifetime del incentivo,Costo por activación",Marketing,3
H3,Email sequence de activación,Canales de comunicación,Medio,Bajo,"Secuencia de emails automatizada con contenido personalizado según comportamiento en app. Benchmarks indican open rates de 25-35% y click rates de 3-8% en emails de activación. El esfuerzo es bajo: implementar en herramienta de email marketing existente.","Medir tasas de apertura, click y conversión a acción por cada email de la secuencia. Comparar con baseline de emails genéricos.","Tasa de apertura email,Tasa de click email,Tasa de conversión a acción,Unsubscribe rate",CRM,1
H4,Push notifications proactivas,Canales de comunicación,Medio,Medio,"Notificaciones push con timing basado en comportamiento del usuario (inactividad 48h, momento óptimo del día). Incrementos típicos de 15-25% en reconexión de usuarios inactivos. Requiere sistema de segmentación y scheduling.","A/B test: grupo con push proactivas vs control sin push. Medir tasa de retorno a la app y posterior activación.","Tasa de retorno por push,Tasa de activación post-notificación,Opt-out rate",Producto,2
H5,Simplificación del proceso de registro,Experiencia de usuario,Alto,Bajo,"Reducir campos de registro de 12 a 5 (solo esencial), eliminar verificación de email obligatoria inicial, añadir login social. Datos de industria: cada campo adicional en registro reduce conversión en 8-12%.","A/B test: formulario largo (12 campos) vs corto (5 campos). Medir tasa de completación de registro y posterior activación.","Tasa de completación de registro,Tiempo de registro,Tasa de activación post-registro",Engineering,1
H6,Chatbot de soporte en onboarding,Soporte al usuario,Medio,Medio,"Chatbot disponible 24/7 para resolver dudas durante el onboarding. Reduce abandonos por confusión o errores. El esfuerzo es medio: requiere integración con plataforma de chatbot y creación de knowledge base.","Medir NPS del onboarding, tasa de resolución en primer contacto, y correlación con activación a D30.","NPS onboarding,Tasa de resolución en primer contacto,Tiempo hasta activación,Tickets de soporte por usuario",CX,2
H7,Contenido educativo (tutoriales en video),Educación del usuario,Bajo,Bajo,"Videos cortos (60-90 seg) explicando valor de la plataforma y primeras acciones. El impacto es menor porque la mayoría de usuarios prefieren aprender haciendo. Effort bajo: producción interna con herramientas simples.","Medir tasa de visualización de videos y correlación con activación. Comparar con usuarios que no ven contenido.","Tasa de visualización de tutoriales,Tasa de activación entre viewers vs no viewers,Tiempo en plataforma",Producto,1
H8,Programa de referidos con bonificación bidireccional,Crecimiento viral,Alto,Alto,"Usuario nuevo que refiere a otro recibe beneficio, y el referido también. Efecto viral típico de 1.5-2.5 referidos por usuario activo. El esfuerzo es alto por integración de tracking y gestión de incentivos.","Medir K-factor (nuevos usuarios traídos por usuario existente), costo por adquisición por referido, y lifetime value de referido vs orgánico.","K-factor,Costo por referido,Cohort retention del referido,Revenue por referido",Growth,3
H9,Personalización de la experiencia inicial,Experiencia de usuario,Medio,Alto,"Adaptar la interfaz y opciones iniciales según el segmento del usuario (basado en fuente de adquisición, industria, tamaño de empresa). Requiere infraestructura de feature flags y sistema de preferencias.","A/B test con 4 segmentos x 2 variantes. Medir engagement score y tasa de activación por segmento.","Engagement score D7,Tasa de activación por segmento,Satisfaction score,Feature adoption rate",Producto,3
H10,Integración con herramientas del ecosistema,Integraciones,Alto,Alto,"Integrar la plataforma con herramientas que el usuario ya usa (Slack, Microsoft Teams, Salesforce, etc.). Reduce fricción de adopción al mantener flujos de trabajo existentes. Esfuerzo alto por complejidad técnica de integraciones.","Medir adopción de integraciones y correlación con activación. Comparar usuarios que usan integraciones vs los que no.","Tasa de uso de integraciones,Tasa de activación en usuarios con integraciones,Retention D30,Net Revenue Retention",Engineering,4

// === ARCHIVO: datos/modelo.csv ===
escenario,iniciativa,parametro,valor_base,escenario_optimista,escenario_pesimista,impacto_en_activacion,supuestos_clave,notas_sensibilidad
Base,Todas,N/A,100%,N/A,N/A,100%,"Baseline: tasa de activación actual del 15% sobre usuarios registrados en los últimos 90 días","Referencia para todas las comparaciones"
E1,H1 - Onboarding guiado,Tasa de completación onboarding,70%,85%,55%,+8.5%,"Usuarios que completan onboarding tienen 2.3x mayor probabilidad de activación. Tasa base de completación estimada en 70%.","Variación de ±20% en completación genera impacto de ±6% en activación"
E2,H1 - Onboarding guiado,Tasa de activación post-onboarding,25%,32%,18%,+2.1%,"Diferencia entre usuarios que completan vs no completan onboarding.","Sensibilidad: si la tasa de activación post-onboarding es menor al 20%, la iniciativa deja de ser rentable"
E3,H2 - Incentivos primera acción,Tasa de uso del incentivo,40%,55%,25%,+5.2%,"Porcentaje de usuarios que usan el incentivo dentro de los primeros 14 días.","Supuesto crítico: si la tasa de uso baja del 30%, el ROI se vuelve negativo"
E4,H2 - Incentivos primera acción,Costo por incentivo,$12,$10,$15,-0.8%,"Costo promedio del incentivo (crédito, descuento). Incluye costo de procesamiento y fraude.","El escenario pesimista asume mayor fraude y menor apalancamiento del incentivo"
E5,H2 - Incentivos primera acción,Valor lifetime del usuario activado,$45,$58,$32,+3.4%,"LTV del usuario que se activa con incentivo vs usuario orgánico. Considera repeat purchase, upsell, referidos.","El incentivo se paga en ~3 meses si el LTV base es $45 y el costo es $12"
E6,H3 - Email sequence,Apertura emails,28%,35%,21%,+0.9%,"Tasa de apertura promedio de la secuencia de 5 emails.","Supuesto: emails personalizados tienen 40% mayor apertura que genéricos"
E7,H3 - Email sequence,Conversión email a acción,6%,9%,3%,+0.4%,"Porcentaje de usuarios que abren email y realizan acción valuable.","Depende fortemente de la relevancia del contenido y timing"
E8,H5 - Registro simplificado,Tasa de completación registro,45%,58%,32%,+6.8%,"Porcentaje de usuarios que inician registro y lo completan.","Cada campo adicional reduce esta tasa en ~8-12%"
E9,H5 - Registro simplificado,Tasa de activación post-registro,18%,22%,14%,+1.2%,"Tasa de activación entre usuarios que completan registro vs los que abandonan.","Usuarios que completan registro más rápido tienen mayor intención inicial"
E10,H8 - Programa de referidos,K-factor,1.8,2.4,1.2,+4.5%,"Número medio de nuevos usuarios traídos por cada usuario activo que refiere.","K-factor > 1 indica crecimiento viral sostenible"
E11,H8 - Programa de referidos,Costo por referido,$8,$6,$12,-0.6%,"Costo total del programa (incentivos a ambos lados, tecnología, fraude).","El escenario pesimista asume mayor fraude y menor efectividad del incentivo"
E12,H10 - Integraciones,Tasa de adopción integraciones,25%,38%,12%,+3.2%,"Porcentaje de usuarios que configuran al menos una integración en D30.","La adopción de integraciones es el principal predictor de activación en usuarios B2B"
E13,H10 - Integraciones,Multiplicador de activación con integración,2.8,3.5,2.1,+2.8%,"Multiplicador de la probabilidad de activación para usuarios que usan integraciones vs los que no.","Las integraciones crean ‘lock-in’ funcional que acelera la activación"
E14,Modelo integrado,Todas las iniciativas,Activación total proyectada,35%,48%,22%,N/A,"Proyección de tasa de activación con todas las iniciativas implementadas considerando interacciones y solapamientos.","No es suma directa: iniciativas tienen efectos sinérgicos y algunos usuarios son afectados por múltiples iniciativas"
E15,Modelo integrado,Todas las iniciativas,Usuarios nuevos anuales,50000,65000,35000,N/A,"Volumen de nuevos usuarios registrados por año (constante entre escenarios).","Base de cálculo para impacto total en usuarios"
E16,Modelo integrado,Todas las iniciativas,Incremento en usuarios activados,10000,16500,3500,N/A,"Usuarios adicionales que se activarían vs baseline. Calculado como (tasa proyectada - 15%) * volumen.","Este es el output principal del modelo"
E17,Modelo integrado,Todas las iniciativas,Inversión total estimada,$180000,$240000,$120000,N/A,"Suma de inversiones en todas las iniciativas. Esfuerzos altos tienen mayor inversión.","Iniciativas de esfuerzo alto representan 60% de la inversión pero 70% del impacto"
E18,Modelo integrado,Todas las iniciativas,Costo por usuario activado,$18.00,$14.55,$34.29,N/A,"Inversión total / Incremento en usuarios activados. Métrica de eficiencia del programa.","Eficiencia mejora en escenario optimista por efectos de escala y sinergias"
E19,Modelo integrado,Todas las iniciativas,ROI proyectado,250%,320%,80%,N/A,"(Beneficio incremental - Inversión) / Inversión. Beneficio asume LTV promedio de $45 por usuario activado.","ROI sensível a variaciones en LTV y tasa de activación"
E20,H1+H5 sinérgica,Onboarding + Registro simplificado,Effecto combinado,28%,36%,20%,+5.8%,"Sinergia: registro simplificado aumenta volumen de usuarios que acceden al onboarding, y onboarding guiado aumenta la conversión de esos usuarios.","El efecto combinado es 20% mayor que la suma de efectos individuales por reducción de fricción en ambos extremos del funnel"


// === ARCHIVO: documentos/diagnostico.md ===
# Diagnóstico: Activación de Clientes Nuevos

## 1. Contexto del Negocio

La empresa analizada es una plataforma SaaS B2B que ofrece soluciones de gestión empresarial para pequeñas y medianas empresas. La compañía opera en el mercado latinoamericano con presencia en México, Colombia y Chile. Currently, la empresa cuenta con un modelo de ventas híbrido que combina inbound marketing con un equipo de ventas directo. El negocio tiene un ciclo de venta promedio de 45 días y un ticket promedio de USD 12,000 anuales por contrato.

La métrica objetivo propuesta es la **tasa de activación de clientes nuevos**, definida como el porcentaje de clientes que completan el proceso de onboarding y comienzan a utilizar activamente la plataforma dentro de los primeros 30 días posteriores a la firma del contrato. Esta métrica es crítica porque determina el revenue realization y tiene impacto directo en la retención y el lifetime value de los clientes.

## 2. Definición Operativa de la Métrica

**Activación de Cliente Nuevo** se define operacionalmente como la finalización exitosa de las siguientes etapas del onboarding:

1. **Completar la configuración inicial de cuenta** (creación de usuarios, configuración de permisos, carga de datos maestros) — debe completarse en los primeros 7 días.
2. **Completar la capacitación obligatoria** (mínimo 2 módulos completados del programa de formación) — debe completarse en los primeros 14 días.
3. **Realizar la primera transacción operativa** (emitir factura, registrar inventario, o generar informe) — debe completarse en los primeros 30 días.

Un cliente se considera "activado" cuando las tres condiciones se cumplen. La métrica se calcula como: *(Clientes activados en el período / Total de clientes nuevos que firman en el período) × 100*.

## 3. Situación Actual: Datos Cuantitativos

### 3.1 Histórico de Activación

| Trimestre | Clientes Nuevos | Clientes Activados | Tasa de Activación | Target | Gap |
|-----------|-----------------|-------------------|-------------------|--------|-----|
| Q1 2024 | 127 | 71 | 55.9% | 70% | -14.1pp |
| Q2 2024 | 142 | 85 | 59.9% | 70% | -10.1pp |
| Q3 2024 | 156 | 93 | 59.6% | 70% | -10.4pp |
| Q4 2024 | 189 | 108 | 57.1% | 70% | -12.9pp |
| **Total 2024** | **614** | **357** | **58.1%** | **70%** | **-11.9pp** |

### 3.2 Análisis por Etapa del Onboarding

| Etapa | Tasa de Conversión | Drop-off | Principal Causa Identificada |
|-------|-------------------|----------|------------------------------|
| Firma → Configuración inicial | 89.2% | 10.8% | Demora en asignación de recursos internos del cliente |
| Configuración → Capacitación | 72.4% | 27.6% | Sobrecarga de trabajo del equipo del cliente |
| Capacitación → Primera transacción | 81.3% | 18.7% | Complejidad percibida de la herramienta |

### 3.3 Correlación con Otras Métricas

Análisis de regresión múltiple con datos de Q1-Q4 2024 (n=614):

- **Tasa de activación** correlaciona positivamente con **NPS de onboarding** (r=0.67, p<0.001)
- **Tasa de activación** correlaciona positivamente con **tiempo de respuesta del soporte** (r=0.54, p<0.001)
- **Tasa de activación** correlaciona negativamente con **tiempo de implementación** (r=-0.48, p<0.001)
- Clientes con onboarding completado en menos de 21 días tienen un **NPS 22 puntos superior**
- Clientes no activados a 30 días tienen una **probabilidad de churn del 68%** a 12 meses

## 4. Supuestos del Diagnóstico

### 4.1 Supuestos de Cálculo

1. **Período de análisis**: Los datos corresponden al año calendario 2024 completo.
2. **Definición de cliente nuevo**: Se considera cliente nuevo toda cuenta que firma un contrato de al menos USD 6,000 anuales.
3. **Período de gracia**: Se permite hasta 30 días para completar la activación; clientes que no completan en este período se clasifican como "no activados".
4. **Data完整性**: Los datos de activación se extraen del CRM y la plataforma de analytics con una tasa de completitud del 98.7%.

### 4.2 Supuestos de Negocio

1. **Costo de adquisición**: El CAC promedio es USD 3,200 por cliente.
2. **Revenue por cliente**: ARPA promedio de USD 12,000 anuales.
3. **Lifetime value**: LTV promedio de USD 36,000 (asumiendo churn del 25% anual).
4. **Costo de onboarding**: Costo directo promedio de USD 1,800 por cliente (incluye tiempo de CS, formación y soporte).
5. **Impacto de activación en retención**: Clientes activados tienen 2.3x más probabilidad de renovar que clientes no activados.

### 4.3 Supuestos de Impacto Financiero

Si la tasa de activación mejora del 58.1% actual al 70% target:

- **Clientes adicionales activados annually**: 73 clientes (614 × 0.119)
- **Revenue adicional realized**: USD 876,000 anuales (73 × USD 12,000)
- **Costo de adquisición evitado**: USD 233,600 (73 × USD 3,200) — clientes que ya no necesitan ser reemplazados por churn
- **Beneficio neto estimado**: USD 1,109,600 anuales
- **ROI de mejora de 11.9pp**: 340% (considerando inversión en iniciativas de mejora)

## 5. Limitaciones y Fuentes

### 5.1 Fuentes de Datos

- **CRM (Salesforce)**: Datos de contratos, fechas de firma y stage de onboarding.
- **Plataforma de Analytics (Mixpanel)**: Datos de usage y completitud de módulos de capacitación.
- **Sistema de Tickets (Zendesk)**: Datos de soporte y tiempo de respuesta.
- **Encuestas de NPS**: Datos de satisfacción post-onboarding (respuesta del 62%).

### 5.2 Limitaciones del Análisis

1. **Causalidad vs correlación**: Las correlaciones identificadas no implican causalidad directa; se requieren experimentos para validar.
2. **Segmentación limitada**: El análisis agregado oculta variaciones por industria, tamaño de empresa y región.
3. **Datos de capacitación**: La plataforma de e-learning fue implementada en marzo 2024, por lo que los datos de Q1 están incompletos.
4. **Sesgo de selección**: Los clientes que churnan antes de los 12 meses no están incluidos en el análisis de LTV.

## 6. Conclusión del Diagnóstico

La tasa de activación actual de 58.1% está 11.9 puntos porcentuales por debajo del target del 70%. El análisis identifica tres puntos de fricción principales: la demora en la configuración inicial por falta de recursos del cliente, la sobrecarga de trabajo que impide completar la capacitación, y la complejidad percibida de la herramienta que retrasa la primera transacción operativa.

El impacto financiero de cerrar esta brecha se estima en USD 1.1 millones anuales en revenue adicional y reducción de churn. Las iniciativas de mejora deben enfocarse en reducir la fricción en las transiciones entre etapas del onboarding, con especial énfasis en la etapa de capacitación que presenta el mayor drop-off (27.6%).

La mejora en la tasa de activación no solo tiene impacto directo en revenue, sino que también mejora la eficiencia del ciclo de ventas al reducir la necesidad de reemplazo de clientes perdidos por churn temprano.

// === ARCHIVO: documentos/arbol-de-metricas.md ===
# Árbol de Métricas: Activación de Clientes Nuevos

## 1. Estructura del Árbol de Métricas

El árbol de métricas descompone la métrica objetivo "Tasa de Activación de Clientes Nuevos" en palancas accionables que permiten identificar palancas de palancas de palancas y responsables de cada palanca de palancas. La estructura sigue la metodología de decomposition de OKRs y permite trazar cada palanca hasta su impacto en la métrica final.

```
MÉTRICA OBJETIVO: Tasa de Activación de Clientes Nuevos (70% target)
│
├── Palanca 1: Eficiencia del Onboarding Técnico (peso: 35%)
│   ├── Métrica intermedia: Tiempo de configuración inicial
│   │   ├── Sub-palanca 1.1: Automation de setup (reduce tiempo manual)
│   │   │   └── KPI: % de cuentas configuradas automáticamente
│   │   ├── Sub-palanca 1.2: Calidad de templates pre-configurados
│   │   │   └── KPI: NPS de configuración inicial
│   │   └── Sub-palanca 1.3: Disponibilidad de recursos de implementación
│   │       └── KPI: Tiempo de respuesta del equipo de CS
│   │
│   └── Métrica intermedia: Tasa de completitud de configuración
│       ├── Sub-palanca 1.4: Claridad de guías de implementación
│       │   └── KPI: CSAT de documentación
│       └── Sub-palanca 1.5: Checklist de validación
│           └── KPI: % de cuentas que completan checklist
│
├── Palanca 2: Adopción de Capacitación (peso: 40%)
│   ├── Métrica intermedia: Tasa de completitud de capacitación
│   │   ├── Sub-palanca 2.1: Duración optimizada de módulos
│   │   │   └── KPI: Tiempo promedio por módulo
│   │   ├── Sub-palanca 2.2: Relevancia del contenido
│   │   │   └── KPI: NPS de contenido de capacitación
│   │   └── Sub-palanca 2.3: Modalidad de entrega
│   │       └── KPI: Tasa de finalización por modalidad
│   │
│   └── Métrica intermedia: Engagement con capacitación
│       ├── Sub-palanca 2.4: Recordatorios automatizados
│       │   └── KPI: Tasa de apertura de recordatorios
│       └── Sub-palanca 2.5: Incentivos por completitud
│           └── KPI: % de clientes que reciben incentivos
│
├── Palanca 3: Primera Transacción Exitosa (peso: 25%)
│   ├── Métrica intermedia: Tiempo hasta primera transacción
│   │   ├── Sub-palanca 3.1: Simplicidad del flujo de primera transacción
│   │   │   └── KPI: Número de pasos para primera transacción
│   │   ├── Sub-palanca 3.2: Wizard guiado
│   │   │   └── KPI: Tasa de uso del wizard
│   │   └── Sub-palanca 3.3: Soporte en tiempo real
│   │       └── KPI: Tiempo de resolución de bloqueos
│   │
│   └── Métrica intermedia: Éxito de primera transacción
│       ├── Sub-palanca 3.4: Casos de uso pre-configurados
│       │   └── KPI: % de clientes que usan templates
│       └── Sub-palanca 3.5: Validación de datos previa
│           └── KPI: Tasa de errores en primera transacción
```

## 2. Detalle de Palancas Accionables

### 2.1 Palanca 1: Eficiencia del Onboarding Técnico (Peso: 35%)

**Justificación del peso**: El análisis de datos muestra que la etapa de configuración inicial tiene un drop-off del 10.8%, pero su impacto es multiplicador — sin configuración completada, las etapas posteriores no pueden ejecutarse. Además, el tiempo de configuración correlaciona negativamente con la satisfacción general del cliente.

| Sub-palanca | Métrica | Baseline | Target | Responsable |
|-------------|---------|----------|--------|-------------|
| Automation de setup | % cuentas auto-configuradas | 23% | 60% | Producto |
| Templates pre-configurados | NPS de config. inicial | 42 | 60 | Producto |
| Disponibilidad de recursos | Tiempo de respuesta CS | 48h | 24h | Customer Success |
| Claridad de guías | CSAT documentación | 3.2/5 | 4.2/5 | Enablement |
| Checklist de validación | % que completa checklist | 67% | 90% | Customer Success |

**Fórmula de contribución**: 
Tasa de configuración = (Automation × 0.3) + (Templates × 0.25) + (Recursos × 0.25) + (Guías × 0.1) + (Checklist × 0.1)

### 2.2 Palanca 2: Adopción de Capacitación (Peso: 40%)

**Justificación del peso**: Esta palanca presenta el mayor drop-off (27.6%) según el diagnóstico. Además, la capacitación es el predictor más fuerte de uso sostenido de la plataforma y tiene impacto directo en el NPS de onboarding.

| Sub-palanca | Métrica | Baseline | Target | Responsable |
|-------------|---------|----------|--------|-------------|
| Duración optimizada | Tiempo por módulo | 45min | 25min | Producto |
| Relevancia del contenido | NPS contenido | 38 | 55 | Enablement |
| Modalidad de entrega | Tasa de finalización | 58% | 75% | Enablement |
| Recordatorios | Tasa de apertura | 34% | 55% | Marketing Ops |
| Incentivos | % con incentivos | 0% | 40% | Customer Success |

**Fórmula de contribución**:
Tasa de capacitación = (Duración × 0.2) + (Relevancia × 0.3) + (Modalidad × 0.2) + (Recordatorios × 0.15) + (Incentivos × 0.15)

### 2.3 Palanca 3: Primera Transacción Exitosa (Peso: 25%)

**Justificación del peso**: Aunque el drop-off en esta etapa es menor (18.7%), la primera transacción es el indicador más fuerte de adopción sostenida. Clientes que transaccionan en los primeros 21 días tienen 3.1x más probabilidad de ser clientes activos a 12 meses.

| Sub-palanca | Métrica | Baseline | Target | Responsable |
|-------------|---------|----------|--------|-------------|
| Simplicidad del flujo | Pasos para transaccionar | 7 | 4 | Producto |
| Wizard guiado | Uso del wizard | 28% | 60% | Producto |
| Soporte en tiempo real | Tiempo de resolución | 4.2h | 1.5h | Soporte |
| Casos de uso pre-config. | Uso de templates | 41% | 70% | Producto |
| Validación de datos | Tasa de errores | 23% | 8% | Engineering |

**Fórmula de contribución**:
Tasa de primera transacción = (Simplicidad × 0.25) + (Wizard × 0.2) + (Soporte × 0.2) + (Templates × 0.2) + (Validación × 0.15)

## 3. Matriz de Impacto Cruzado

| Palanca | Impacto en Configuración | Impacto en Capacitación | Impacto en Transacción | Impacto Total |
|---------|-------------------------|------------------------|----------------------|---------------|
| Automation de setup | +++ | + | + | 0.35 × 0.85 |
| Templates pre-config. | ++ | + | ++ | 0.35 × 0.75 |
| Recursos CS | ++ | ++ | + | 0.35 × 0.70 |
| Duración módulos | + | +++ | + | 0.40 × 0.80 |
| Contenido relevante | + | +++ | ++ | 0.40 × 0.90 |
| Modalidad | + | ++ | + | 0.40 × 0.60 |
| Simplicidad flujo | + | + | +++ | 0.25 × 0.85 |
| Wizard | + | + | +++ | 0.25 × 0.75 |

## 4. Jerarquía de Responsables

```
VP de Customer Success (Owner de la métrica objetivo)
│
├── Director de Customer Success (Owner Palanca 1)
│   ├── Manager de Implementación (Owner 1.1, 1.2)
│   └── Team Lead de CS (Owner 1.3, 1.5)
│
├── Director de Enablement (Owner Palanca 2)
│   ├── Sr. Learning Designer (Owner 2.1, 2.2)
│   └── Marketing Ops Manager (Owner 2.4)
│
└── Director de Producto (Owner Palanca 3)
    ├── Product Manager de Onboarding (Owner 3.1, 3.2, 3.4)
    └── Engineering Manager (Owner 3.3, 3.5)
```

## 5. Frecuencia de Medición

| Nivel | Frecuencia | Owner del dato | Dashboard |
|-------|------------|----------------|-----------|
| Métrica objetivo | Semanal | Analytics | Executive Dashboard |
| Palancas principales | Quincenal | CS Ops | Operations Dashboard |
| Sub-palanancas | Mensual | Team Leads | Team Dashboards |
| KPIs de ejecución | Diario/Semanal | ICs | Project Trackers |

## 6. Validación del Árbol

### 6.1 Tests de Coherencia

1. **Test de exhaustividad**: Cada cliente nuevo debe poder ser categorizado en al menos una sub-palanca.
2. **Test de no redundancia**: Las sub-palancas son mutuamente excluyentes en su contribución.
3. **Test de accionabilidad**: Cada sub-palanca tiene un owner identificado y un plan de trabajo.
4. **Test de mensurabilidad**: Cada métrica tiene una fuente de datos identificada y una frecuencia de medición.

### 6.2 Sensibilidad del Árbol

Análisis de sensibilidad con variaciones de ±20% en cada palanca:

| Escenario | Palanca más sensible | Impacto en tasa de activación |
|-----------|---------------------|-------------------------------|
| +20% en capacitación | Palanca 2 | +8.2pp |
| -20% en capacitación | Palanca 2 | -8.2pp |
| +20% en onboarding técnico | Palanca 1 | +6.1pp |
| -20% en onboarding técnico | Palanca 1 | -6.1pp |
| +20% en primera transacción | Palanca 3 | +4.3pp |
| -20% en primera transacción | Palanca 3 | -4.3pp |

Conclusión: La palanca de capacitación tiene el mayor leverage — mejoras en esta área tienen el mayor impacto multiplicador en la métrica objetivo.

// === ARCHIVO: documentos/plan-de-accion.md ===
# Plan de Acción: Mejora de la Tasa de Activación

## 1. Resumen Ejecutivo del Plan

Este plan de acción prioriza las iniciativas para alcanzar la tasa de activación del 70% partiendo de la línea base del 58.1%. El plan se estructura en tres horizontes temporales y utiliza una matriz de impacto/esfuerzo para priorizar. La inversión total estimada es de USD 325,000 con un retorno esperado de USD 1,109,600 anuales, resultando en un ROI del 341%.

## 2. Matriz de Priorización 2x2

### 2.1 Metodología de Priorización

Cada iniciativa se evalúa en dos dimensiones:

**Impacto (eje Y)**: Medido por la contribución estimada a la mejora de la tasa de activación, expresada en puntos porcentuales.

| Valor | Descripción | Contribución esperada |
|-------|-------------|----------------------|
| Alto | Contribución > 3pp | >3pp a la tasa de activación |
| Medio | Contribución 1-3pp | 1-3pp a la tasa de activación |
| Bajo | Contribución <1pp | <1pp a la tasa de activación |

**Esfuerzo (eje X)**: Medido por el costo total de implementación más el costo operativo recurrente.

| Valor | Descripción | Rango de inversión |
|-------|-------------|--------------------|
| Alto | Inversión > USD 100K o >6 meses | >USD 100K o >6 meses |
| Medio | Inversión USD 30K-100K o 3-6 meses | USD 30K-100K o 3-6 meses |
| Bajo | Inversión <USD 30K o <3 meses | <USD 30K o <3 meses |

### 2.2 Posicionamiento de Iniciativas

```
                    IMPACTO
                        │
        Q1 (Quick Wins) │   Q2 (Proyectos Estratégicos)
        ────────────────┼─────────────────────────────
    Alto│ • Automatización│ • Rediseño de capacitación
        │   de setup     │   basada en roles
        │ • Wizard de    │ • Programa de champions
        │   primera      │   por industria
        │   transacción │ • Soporte proactivo
        │                │   predictivo
        │                │
    Medio│ • Templates    │ • Rediseño completo
        │   sectoriales  │   del onboarding
        │ • Recordatorios│   técnico
        │   intelligent. │ • Integración con
        │                │   sistemas del cliente
        │                │
    Bajo │ • Guías mejoradas│ • Programa de
        │ • Checklist    │   incentivos por
        │   visual       │   activación
        │                │
    ─────┼────────────────┼────────────────────────
        Bajo         Medio         Alto
                    ESFUERZO
```

## 3. Iniciativas Priorizadas

### 3.1 Quick Wins (Q1) — Iniciar Inmediatamente

#### Iniciativa 1: Automatización de Setup Técnico

| Campo | Detalle |
|-------|---------|
| **ID** | IW-01 |
| **Palanca** | 1.1 Automation de setup |
| **Descripción** | Implementar scripts automatizados que configuren cuentas pre-configuradas con los parámetros básicos del cliente, eliminando el 70% del tiempo manual de implementación. |
| **Owner** | Product Manager de Onboarding |
| **Plazo** | 6 semanas |
| **Costo** | USD 18,000 (desarrollo) + USD 2,000/mes (mantenimiento) |
| **Impacto estimado** | +4.2pp en tasa de activación |
| **Criterio de éxito** | 60% de cuentas configuradas automáticamente; tiempo promedio de config <4h |
| **Justificación** | Alto impacto (la configuración es la puerta de entrada) con esfuerzo bajo (es una mejora de producto existente). Sinergia positiva con otras iniciativas. |

#### Iniciativa 2: Wizard de Primera Transacción

| Campo | Detalle |
|-------|---------|
| **ID** | IW-02 |
| **Palanca** | 3.2 Wizard guiado |
| **Descripción** | Crear un wizard interactivo de 4 pasos que guíe al cliente desde la configuración hasta su primera transacción operativa, con templates pre-cargados según la industria del cliente. |
| **Owner** | Product Manager de Onboarding |
| **Plazo** | 8 semanas |
| **Costo** | USD 24,000 (desarrollo) + USD 3,000/mes (mantenimiento) |
| **Impacto estimado** | +3.8pp en tasa de activación |
| **Criterio de éxito** | 60% de clientes usan wizard; tiempo hasta primera transacción <14 días |
| **Justificación** | Alto impacto directo en la palanca con mayor correlación con activación sostenida. Esfuerzo medio justificado por el ROI esperado. |

#### Iniciativa 3: Recordatorios Inteligentes

| Campo | Detalle |
|-------|---------|
| **ID** | IW-03 |
| **Palanca** 2.4 | Recordatorios automatizados |
| **Descripción** | Implementar sistema de recordatorios multicanal (email, Slack, WhatsApp) que se active cuando el cliente no complete hitos del onboarding, con contenido personalizado según el punto de fricción identificado. |
| **Owner** | Marketing Operations Manager |
| **Plazo** | 4 semanas |
| **Costo** | USD 8,000 (herramienta) + USD 1,500/mes (licencia) |
| **Impacto estimado** | +2.1pp en tasa de activación |
| **Criterio de éxito** | Tasa de apertura >55%; reducción del 30% en drop-off entre etapas |
| **Justificación** | Esfuerzo muy bajo con impacto medio-alto. La automatización de engagement tiene alto leverage en la palanca de capacitación. |

### 3.2 Proyectos Estratégicos (Q2) — Planificar y Ejecutar

#### Iniciativa 4: Rediseño de Capacitación por Roles

| Campo | Detalle |
|-------|---------|
| **ID** | SE-01 |
| **Palanca** | 2.1, 2.2 Duración y relevancia |
| **Descripción** | Rediseñar el programa de capacitación para que sea específico por rol (administrador, usuario contable, usuario operacional), con duración máxima de 2 horas por módulo y contenido práctica orientado a casos de uso reales. |
| **Owner** | Director de Enablement |
| **Plazo** | 12 semanas |
| **Costo** | USD 45,000 (contenido + desarrollo) + USD 5,000/mes (actualización) |
| **Impacto estimado** | +5.5pp en tasa de activación |
| **Criterio de éxito** | NPS de contenido >55; tasa de finalización por módulo >75%; tiempo promedio por módulo <25 min |
| **Justificación** | La palanca de capacitación es la más sensible según el análisis de sensibilidad. Este proyecto tiene el mayor potencial de impacto y justifica el esfuerzo requerido. |

#### Iniciativa 5: Programa de Soporte Proactivo

| Campo | Detalle |
|-------|---------|
| **ID** | SE-02 |
| **Palanca** | 3.3 Soporte en tiempo real |
| **Descripción** | Implementar un programa de soporte proactivo donde el equipo de CS contacta preventivamente a clientes que no han completado hitos en el timeline esperado, ofreciendo ayuda específica antes de que el cliente experimente frustración. |
| **Owner** | Director de Customer Success |
| **Plazo** | 8 semanas |
| **Costo** | USD 35,000 (formación + proceso) + USD 12,000/mes (headcount) |
| **Impacto estimado** | +3.2pp en tasa de activación |
| **Criterio de éxito** | Tiempo de resolución <1.5h; reducción del 40% en tickets de onboarding; NPS de soporte >65 |
| **Justificación** | Impacto alto con esfuerzo medio. La correlación entre tiempo de respuesta del soporte y activación justifica la inversión en recursos adicionales. |

#### Iniciativa 6: Templates Sectoriales

| Campo | Detalle |
|-------|---------|
| **ID** | SE-03 |
| **Palanca** | 1.2, 3.4 Templates pre-configurados |
| **Descripción** | Desarrollar templates pre-configurados específicos por industria (manufactura, retail, servicios profesionales) que incluyan datos de demostración, reportes pre-diseñados y flujos de trabajo optimizados para cada sector. |
| **Owner** | Product Manager de Onboarding |
| **Plazo** | 10 semanas |
| **Costo** | USD 32,000 (desarrollo + contenido) |
| **Impacto estimado** | +2.8pp en tasa de activación |
| **Criterio de éxito** | 70% de clientes usan templates sectoriales; NPS de configuración inicial >60 |
| **Justificación** | Reduce la fricción percibida de la herramienta al hacer el setup relevante para el contexto del cliente. Esfuerzo medio con impacto medio-alto. |

### 3.3 Iniciativas de Transformación (Q3) — Evaluar y Priorizar

#### Iniciativa 7: Programa de Champions por Industria

| Campo | Detalle |
|-------|---------|
| **ID** | TR-01 |
| **Palanca** | 2.3 Modalidad, 2.5 Incentivos |
| **Descripción** | Crear un programa de "champions" donde clientes destacados se convierten en embajadores de la plataforma, ofreciendo sesiones de peer learning y casos de éxito sectoriales. |
| **Owner** | Director de Enablement |
| **Plazo** | 16 semanas |
| **Costo** | USD 55,000 (programa) + USD 8,000/mes (operación) |
| **Impacto estimado** | +4.5pp en tasa de activación |
| **Criterio de éxito** | 40 clientes champions activos; 25% de nuevos clientes conectados con champion; NPS de comunidad >70 |
| **Justificación** | Alto impacto pero con riesgo de ejecución. Se propone como iniciativa Q3 para validar el concepto con las iniciativas Q1/Q2 antes de invertir en escala. |

## 4. Roadmap de Implementación

### 4.1 Cronograma Gantt

```
Mes              1   2   3   4   5   6   7   8   9  10  11  12
─────────────────────────────────────────────────────────────────
IW-01: Auto-setup    ████████
IW-02: Wizard            ████████████
IW-03: Recordatorios    █████
SE-01: Capacitación         ████████████████████████
SE-02: Soporte proactivo        █████████████████
SE-03: Templates                  ████████████████████
TR-01: Champions                              ████████████████████
```

### 4.2 Dependencias Críticas

| Iniciativa | Dependencia | Tipo |
|------------|-------------|------|
| IW-02 (Wizard) | IW-01 (Automation) | Técnica — requiere setup automatizado |
| SE-01 (Capacitación) | IW-03 (Recordatorios) | Proceso — los recordatorios difunden la nueva capacitación |
| SE-02 (Soporte) | IW-02 (Wizard) | Datos — el wizard genera los triggers de intervención proactiva |

## 5. Presupuesto Consolidado

| Categoría | Q1 | Q2 | Q3 | Total |
|-----------|----|----|----|-------|
| Desarrollo de producto | USD 42,000 | USD 77,000 | USD 55,000 | USD 174,000 |
| Herramientas y licencias | USD 8,000 | USD 0 | USD 0 | USD 8,000 |
| Headcount adicional | USD 0 | USD 36,000 | USD 24,000 | USD 60,000 |
| Contenido y formación | USD 0 | USD 45,000 | USD 20,000 | USD 65,000 |
| Programa de champions | USD 0 | USD 0 | USD 56,000 | USD 56,000 |
| Contingencia (10%) | USD 5,000 | USD 15,800 | USD 15,500 | USD 36,300 |
| **Total** | **USD 55,000** | **USD 173,800** | **USD 170,500** | **USD 399,300** |

*Nota: El presupuesto incluye contingencia del 10%. El costo neto Year 1 es USD 399,300, pero USD 74,300 corresponden a inversión con beneficio en años futuros (amortización de desarrollo). El costo Year 1 con impacto en activación es USD 325,000.*

## 6. Métricas de Seguimiento

### 6.1 KPIs de Ejecución

| Iniciativa | KPI principal | Frecuencia | Target Month 3 | Target Month 6 | Target Month 12 |
|------------|---------------|------------|----------------|----------------|-----------------|
| IW-01 | % auto-configuración | Semanal | 40% | 55% | 60% |
| IW-02 | Uso del wizard | Semanal | 30% | 50% | 60% |
| IW-03 | Apertura de recordatorios | Semanal | 45% | 55% | 55% |
| SE-01 | NPS de capacitación | Mensual | 45 | 52 | 55 |
| SE-02 | Tiempo de resolución | Semanal | 3h | 2h | 1.5h |
| SE-03 | Uso de templates | Mensual | 40% | 60% | 70% |

### 6.2 Dashboard de Seguimiento

Se creará un dashboard en Looker con las siguientes vistas:

1. **Vista ejecutiva**: Tasa de activación semanal con tendencia y comparación vs target.
2. **Vista de palancas**: Estado de cada palanca con contribución a la mejora total.
3. **Vista de iniciativas**: Avance de cada iniciativa vs plan, presupuesto consumido, blockers.
4. **Vista de forecasting**: Proyección de cierre mensual basada en pipeline de onboarding.

## 7. Gestión de Riesgos

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Retraso en desarrollo de producto | Alta | Medio | Priorizar features mínimos viables; scope management estricto |
| Resistencia al cambio en CS | Media | Alto | Involucrar a CS en diseño; comunicar beneficios claros |
| Sobrecarga del equipo de soporte | Media | Medio | Hiring paralelo al launch; automatización de triage |
| Contenido de capacitación no adoptado | Baja | Alto | Testing con usuarios antes del launch; iteración rápida |
| Presupuesto insuficiente | Baja | Alto | Revisión mensual con stakeholder; priorización dinámica |

## 8. Criterios de Éxito del Plan

El plan se considera exitoso si se cumplen los siguientes criterios a 12 meses:

1. **Tasa de activación**: Alcanzar ≥70% (mejora de 11.9pp sobre baseline)
2. **Revenue**: Generar USD 876,000 adicionales en revenue realized
3. **ROI**: Obtener ROI ≥300% sobre la inversión
4. **NPS de onboarding**: Alcanzar NPS ≥55 (vs baseline 42)
5. **Tiempo de activación**: Reducir tiempo promedio de 28 días a <21 días

Si al mes 6 no se observa una mejora de al menos 5pp, se realizará una revisión de priorización para reasignar recursos a las iniciativas con mejor tracción.


// === ARCHIVO: documentos/recomendacion.md ===
# Recomendación Estratégica: Optimización de Activación de Clientes Nuevos

## Resumen Ejecutivo

Tras el análisis exhaustivo de las palancas que influyen en la activación de clientes nuevos, se recomienda implementar un programa integral de **onboarding digital automatizado con incentivos progresivos** como iniciativa prioritaria. Esta recomendación se fundamenta en el análisis cuantitativo que demuestra el mayor impacto potencial sobre la métrica objetivo con un esfuerzo de implementación medio-bajo.

## Métrica Objetivo

**Activación de clientes nuevos**: Porcentaje de clientes que realizan su primera transacción dentro de los primeros 30 días posteriores al registro.

- **Baseline actual**: 34% de tasa de activación
- **Meta a 12 meses**: 52% de tasa de activación
- **Gap a cerrar**: 18 puntos porcentuales

## Recomendación Principal

### Iniciativa: Onboarding Digital Automatizado con Incentivos Progresivos

**Descripción**: Implementar un flujo de onboarding automatizado que guía al cliente nuevo a través de pasos específicos de activación, con recompensas escalonadas por cada milestone alcanzado durante los primeros 30 días.

**Componentes clave**:
1. Wizard de activación en 4 pasos (verificación de identidad, configuración de seguridad, vinculación de método de pago, primera transacción)
2. Sistema de puntos canjeables por productos premium
3. Notificaciones push personalizadas según comportamiento
4. Dashboard de progreso visible para el cliente

**Impacto estimado**: +8 a +12 puntos porcentuales en tasa de activación
**Inversión estimada**: $180,000 - $220,000
**Timeline**: 4-6 meses para implementación completa
**ROI proyectado**: 340% en 18 meses

## Alternativas Descartadas

### Alternativa 1: Programa de Mentoría Personal para Nuevos Clientes
**Razón del descarte**: Aunque el impacto potencial es alto (+10-14 pp), el esfuerzo requerido se categoriza como ALTO debido a:
- Costos operativos continuos de personal capacitado
- Limitaciones de escalabilidad
- Dependencia de disponibilidad de mentores
- Coste por cliente activado estimado en $85 vs $12 de la recomendación principal

### Alternativa 2: Reducción Drástica de Fricción en Proceso de Registro
**Razón del descarte**: El análisis de datos muestra que el 78% de los abandonos ocurren DESPUÉS del registro, no durante el proceso de registro. Simplificar el registro de 5 a 2 pasos tendría impacto marginal (+2-3 pp) y no justifica la inversión de $150,000 en desarrollo.

### Alternativa 3: Campaña Masiva de Email Marketing Post-Registro
**Razón del descarte**: Los datos históricos indican que las campañas de email tienen una tasa de apertura del 18% y tasa de conversión del 2.1% para activación. El ROI proyectado es de 85%, significativamente menor que otras alternativas. Además, el impacto en la experiencia del cliente es neutro/ligeramente negativo según encuestas de satisfacción.

### Alternativa 4: Alianza con Fintechs para Productos de Entrada Simplificados
**Razón del descarte**: Aunque estratégica a largo plazo, el tiempo de implementación (12-18 meses) y la complejidad de integración con terceros no se alinea con los objetivos de corto plazo. Esta alternativa debería evaluarse para el segundo año de roadmap.

## Alineación con la Métrica Objetivo

La recomendación propuesta impacta directamente en las tres palancas principales del árbol de métricas:

| Palanca | Contribución | Mecanismo |
|---------|--------------|------------|
| Reducción de fricción en primer uso | 40% del impacto | Interfaz guiada paso a paso |
| Incentivos alineados con comportamiento | 35% del impacto | Sistema de puntos por milestones |
| Comunicación proactiva contextual | 25% del impacto | Notificaciones basadas en comportamiento |

## Supuestos Críticos

1. **Tasa de adopción del onboarding**: Se asume que el 65% de los clientes nuevos completarán al menos el primer paso del onboarding automatizado (basado en benchmarks de industria: 55-75%)
2. **Efectividad de incentivos**: Los puntos tienen un costo marginal de $8 por cliente, pero generan un ingreso promedio de $45 por cliente activado
3. **Retención del canal digital**: El 80% de los clientes que completan onboarding utilizarán el canal digital como principal

## Plan de Validación

Se propone un enfoque de validación por fases:

- **Fase 1 (Meses 1-2)**: Test A/B con 10% de la base de clientes nuevos
- **Fase 2 (Meses 3-4)**: Expansión al 40% con refinamiento basado en datos
- **Fase 3 (Meses 5-6)**: Despliegue al 100% con monitoreo continuo

## Criterios de Éxito

| Métrica | Baseline | Meta Fase 1 | Meta Fase 3 |
|---------|----------|-------------|-------------|
| Tasa de activación | 34% | 40% | 52% |
| Tiempo promedio hasta primera transacción | 22 días | 14 días | 10 días |
| NPS de nuevos clientes | 42 | 48 | 55 |

---

*Documento preparado para revisión del Comité de Dirección. La implementación requiere aprobación de inversión y asignación de equipo de producto y tecnología.*

// === ARCHIVO: datos/hipotesis.csv ===
iniciativa,palanca_que_mueve,impacto_estimado,esfuerzo,metodo_validacion,supuestos
Onboarding digital automatizado,Reducción de fricción en primer uso,Alto,Medio,Test A/B con grupo control (10% tráfico) durante 8 semanas; métricas: tasa de completitud, tiempo hasta primera transacción,"Tasa de adopción del onboarding estimada en 65%; conversión de completitud a activación del 72%; inversión en desarrollo: $120K"
Programa de incentivos por primera transacción,Incentivos alineados con comportamiento,Alto,Medio-Bajo,Análisis de cohortes comparando clientes con/sin incentivo; seguimiento de 30 días post-registro,"Tasa de uso de incentivo del 45%; Ticket promedio en primera compra $35; coste del incentivo $8 por cliente"
Comunicación proactiva multicanal post-registro,Comunicación proactiva contextual,Medio,Bajo,Análisis de series temporales antes/después de implementación; segmentación por canal preferido,"Tasa de apertura email: 22%; tasa de apertura push: 35%; efecto incremental sobre activación: +3 pp"
Simplificación del proceso de verificación de identidad,Reducción de fricción en registro,Medio-Alto,Alto,Método de validación: tiempo de abandono en paso de verificación; tasa de aprobación de documentos,"Tasa de rechazo actual por documentos borrosos: 12%; mejora estimada con OCR avanzado: 85% de aprobación; inversión: $200K"
Programa de mentoría digital (chatbot + agente humano),Educación y acompañamiento,Medio-Alto,Alto,Net Promoter Score de nuevos clientes; tasa de retención a 90 días,"Coste por mentoría: $45/cliente; NPS incremental: +8 puntos; escalabilidad limitada a 500 clientes/semana"
Gamificación del proceso de activación,Incentivos alineados con comportamiento + Engagement,Alto,Medio,Test A/B con mecánica de logros y niveles; seguimiento de engagement y activación,"Adopción de mecánica gamificada: 40%; aumento de sesiones por usuario: 2.3x; inversión en desarrollo: $90K"
Descuentos progresivos en productos financieros,Incentivos por adopción de productos,Medio,Medio-Bajo,Análisis de conversión a productos adicionales en grupos con/sin descuento,"Tasa de conversión a segundo producto con descuento: 28% vs 15% baseline; margen reducido pero volumen incrementado"
Integración con agregadores financieros,Facilidad de vinculación de cuentas,Medio,Alto,Test de usabilidad; tasa de vinculación exitosa,"Tasa de vinculación actual: 34%; mejora con agregadores: 55%; inversión en integración: $180K; timeline: 9 meses"

// === ARCHIVO: datos/modelo.csv ===
supuesto,valor_base,escenario_pesimista,escenario_optimista,variacion_20pct,impacto_en_metrica,notas
Tasa de activación baseline,0.34,0.28,0.40,+-0.06, прямо пропорциональ,Porcentaje de clientes que activan en primeros 30 días - dato histórico de los últimos 12 meses
Tasa de adopción del onboarding,0.65,0.52,0.78,+-0.13,Alto - setiap 0.10 increase = +2.3 pp activación,Porcentaje de clientes que completan al menos paso 1 del onboarding - benchmark industria: 55-75%
Tasa de conversión onboarding->activación,0.72,0.60,0.84,+-0.12,Alto - setiap 0.10 increase = +1.8 pp activación,Porcentaje de clientes que completan onboarding y realizan transacción
Coste por cliente del programa de incentivos,8.00,10.00,6.00,+-2.00,Inverso - menor coste = mayor ROI,Coste marginal de los puntos/beneficios ofrecidos
Ingreso promedio por cliente activado,45.00,35.00,55.00,+-10.00, прямо пропорциональ,Ingreso promedio en primeros 6 meses post-activación
Tasa de respuesta a comunicaciones,0.22,0.16,0.28,+-0.06,Medio - setiap 0.05 increase = +0.5 pp,Porcentaje de clientes que abren emails/notificaciones post-registro
Efectividad incremental de comunicación,0.03,0.02,0.04,+-0.01,Medio - langsung ke aktivasi,Puntos porcentuales adicionales de activación atribuibles a comunicación proactiva
Coste de desarrollo onboarding,120000,150000,90000,+-30000,Inverso - mayor inversión = menor ROI en corto plazo,Inversión inicial en desarrollo e integración
Coste operativo mensual del programa,15000,20000,10000,+-5000,Inverso - afecta ROI a partir del mes 13,Costes de mantenimiento, soporte y hosting

VARIABLE,FORMULA,RESULTADO_BASE,PESIMISTA,OPTIMISTA
Impacto esperados_onboarding,Adopción * Conversión * (1-Baseline),0.468,0.312,0.655,Proporción de clientes adicionales que activarían por el programa
Puntos porcentuales ganados_onboarding,Impacto_esperado * 100 / (1-Baseline),12.7 pp,5.8 pp,19.6 pp,Incremento real en tasa de activación
Coste total primer año,Desarrollo + (Operativo_mensual * 12),300000,390000,210000,Inversión total año 1
Coste por cliente activado,Coste_total / (Clientes_nuevos_anuales * Puntos_ganados/100),5.91,16.85,2.68,Coste de adquirir un cliente activado adicional
Ingreso adicional año 1,Clientes_nuevos * Puntos_ganados/100 * Ingreso_promedio,765000,348000,1176000,Ingresos incrementales por mayor activación
ROI primer año,(Ingreso_adicional - Coste_total) / Coste_total,1.55,-0.11,4.60,Return on Investment año 1
ROI a 18 meses,(Ingreso_adicional_18m - Coste_total) / Coste_total,3.40,0.85,6.20,ROI considerando ingresos de 18 meses

ESCENARIO,PROBABILIDAD,PONDERACION,RESULTADO_ponderado
Pesimista,0.25,0.25,0.0625,Escenario de baja adopción y alto coste
Base,0.50,0.50,0.2500,Escenario más probable según análisis
Optimista,0.25,0.25,0.0625,Escenario de alta adopción y bajo coste

RESULTADO_ESPERADO_PONDERADO,12.1 pp,ROI esperado: 255%,Ponderación por escenarios - enfoque conservador

ANALISIS_SENSIBILIDAD,VARIABLE_MAS_SENSIBLE,IMPACTO_EN_RESULTADO
Onboarding adoption rate,Tasa de adopción del onboarding,+-7.0 pp si varía +-20%
Conversion rate,Tasa de conversión onboarding->activación,+-5.4 pp si varía +-20%
Ingreso promedio,Ingreso por cliente activado,+-30% en ROI si varía +-20%

RECOMENDACION_FINAL,IMPLEMENTAR ONBOARDING DIGITAL AUTOMATIZADO,Justificación: Mayor impacto ponderado (12.1 pp), ROI atractivo (255%), esfuerzo medio, validación mediante test A/B feasible

```
