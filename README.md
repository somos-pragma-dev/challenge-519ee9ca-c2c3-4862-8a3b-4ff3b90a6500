# Diseño y priorización de iniciativas para aumentar la activación de clientes nuevos

La empresa necesita aumentar la activación de clientes nuevos. Para lograrlo, se requiere descomponer la métrica objetivo en palancas accionables y priorizarlas por impacto y esfuerzo con supuestos explícitos. El objetivo es diseñar un árbol de métricas que guíe la toma de decisiones y priorice las iniciativas más efectivas.

## Informacion General

| Campo | Valor |
|-------|-------|
| **Tema** | Árbol de métricas y priorización de iniciativas |
| **Nivel** | advanced-l2 |
| **Tipo** | mixed |
| **Tiempo estimado** | 10 horas |

## Fases del Reto

### Fase 0: Configuración del Proyecto

**Objetivo:** Obtener el proyecto base funcional enviando el Código Base a un asistente de IA, que lo analizará, corregirá errores y generará un ZIP listo para usar.

**Tiempo estimado:** 15-30 minutos

**Instrucciones:**

- Asegúrate de tener instalado para ejecutar el proyecto: Un IDE o editor de código.
- Copia todo el contenido del campo **Código Base** de este reto — incluyendo el texto de instrucciones que aparece al inicio.
- Abre un asistente de IA (Claude en claude.ai, ChatGPT o Gemini — se recomienda Claude), pega el contenido copiado en el chat y envíalo.
- El asistente analizará los archivos, corregirá errores y generará un archivo ZIP descargable. Descárgalo y extráelo en la carpeta donde quieras trabajar.
- Verifica que el proyecto arranca sin errores.

**Entregable:** El proyecto compila/arranca sin errores.

<details>
<summary>Pistas de conocimiento</summary>

- Copia el Código Base completo incluyendo el texto de instrucciones al inicio — esas instrucciones le indican al asistente exactamente qué hacer con los archivos.
- Si el asistente no genera el ZIP automáticamente al terminar el análisis, escríbele: "genera el ZIP ahora".
- Si el proyecto tiene errores al arrancar, comparte el mensaje de error con el mismo asistente para que lo corrija.

</details>

### Fase 1: Identificación de métricas clave

**Objetivo:** Identificar las métricas clave que influyen en la activación de clientes nuevos.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Enumera las métricas relevantes para la activación de clientes nuevos.
- Define cada métrica y su importancia en el proceso de activación.

**Entregable:** Lista de métricas clave con definiciones y relevancia.

<details>
<summary>Pistas de conocimiento</summary>

- Considera métricas como tasa de conversión, tiempo de activación, engagement inicial, etc.

</details>

### Fase 2: Descomposición de métricas en palancas accionables

**Objetivo:** Descomponer cada métrica en palancas accionables.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Para cada métrica identificada, descompónela en palancas accionables.
- Describe cómo cada palanca puede influir en la métrica.

**Entregable:** Desglose de métricas en palancas accionables con descripciones.

<details>
<summary>Pistas de conocimiento</summary>

- Piensa en cómo cada palanca puede ser implementada y medida.

</details>

### Fase 3: Priorización de iniciativas

**Objetivo:** Priorizar las iniciativas basadas en impacto y esfuerzo.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Evalúa cada palanca en términos de impacto y esfuerzo.
- Prioriza las iniciativas con supuestos explícitos.

**Entregable:** Lista de iniciativas priorizadas con supuestos explícitos.

<details>
<summary>Pistas de conocimiento</summary>

- Considera el ROI potencial de cada iniciativa y el esfuerzo requerido para implementarla.

</details>

### Fase 4: Diseño del árbol de métricas

**Objetivo:** Diseñar un árbol de métricas que guíe la toma de decisiones.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Crea un árbol de métricas que incluya las métricas clave, las palancas accionables y las iniciativas priorizadas.
- Asegúrate de que el árbol sea claro y fácil de entender.

**Entregable:** Árbol de métricas diseñado.

<details>
<summary>Pistas de conocimiento</summary>

- Utiliza un formato visual para representar el árbol de métricas.

</details>

## Dimensiones Evaluadas

- **queEs**: ¿Qué es una métrica clave y por qué es importante en el proceso de activación de clientes nuevos?
- **paraQueSirve**: ¿Para qué sirve descomponer una métrica en palancas accionables?
- **comoSeUsa**: ¿Cómo se pueden usar las palancas accionables para influir en las métricas?
- **erroresComunes**: ¿Cuáles son los errores comunes al priorizar iniciativas basadas en impacto y esfuerzo?
- **queDecisionesImplica**: ¿Qué decisiones implica la priorización de iniciativas y cómo se pueden justificar con supuestos explícitos?

## Criterios de Evaluacion

- Identificación correcta de métricas clave.
- Descomposición efectiva de métricas en palancas accionables.
- Priorización adecuada de iniciativas con supuestos explícitos.
- Diseño claro y comprensible del árbol de métricas.

## Como trabajar con un asistente de IA

Hay dos caminos, elegi uno:

- **AGENTS.md** (recomendado) — instrucciones nativas del repo. Abri esta carpeta con tu agente local (Claude Code, Cursor, Codex, Copilot, Gemini) y las carga solo. Sabe que archivos faltan y con que comando se verifica, y completa el scaffold escribiendo en disco.
- **PROMPT_MEJORA.md** — para copiar y pegar en un chat (claude.ai, ChatGPT). Devuelve un ZIP con el proyecto. Sirve si no tenes un agente en el IDE.

Ninguno de los dos resuelve las fases del reto: eso es tu trabajo.

## Verificacion

El proyecto esta listo para trabajar cuando este comando corre sin errores:

```bash
python3 -c "import csv,glob; [list(csv.DictReader(open(f))) for f in glob.glob('*.csv')]"
```

---

*Reto generado automaticamente por Challenge Generator - Pragma*
