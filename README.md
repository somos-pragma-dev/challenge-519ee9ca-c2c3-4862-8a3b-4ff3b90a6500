# Diseño y Priorización de Árbol de Métricas

Tu equipo de consultoría de negocio necesita descomponer una métrica objetivo en palancas accionables y priorizarlas por impacto y esfuerzo. La métrica objetivo es 'activación de clientes nuevos'. Debes diseñar un árbol de métricas que represente las diferentes iniciativas que pueden influir en esta métrica y priorizarlas basándote en supuestos explícitos sobre su impacto y el esfuerzo requerido para implementarlas.

## Informacion General

| Campo | Valor |
|-------|-------|
| **Tema** | Árbol de métricas y priorización de iniciativas |
| **Nivel** | advanced-l2 |
| **Tipo** | practical |
| **Tiempo estimado** | 8 horas |

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

### Fase 1: Definición de la Métrica Objetivo

**Objetivo:** Clarificar y definir la métrica objetivo 'activación de clientes nuevos' en términos del negocio.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Identifica y describe la métrica objetivo 'activación de clientes nuevos' en términos del negocio. Incluye una definición clara y los supuestos subyacentes.

**Entregable:** Descripción clara y detallada de la métrica objetivo 'activación de clientes nuevos'.

<details>
<summary>Pistas de conocimiento</summary>

- Considera las diferentes formas en que un cliente puede ser considerado 'activado' y los supuestos que esto implica.

</details>

### Fase 2: Descomposición de la Métrica en Palancas Accionables

**Objetivo:** Descomponer la métrica objetivo en diferentes iniciativas o palancas accionables.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Descompone la métrica objetivo 'activación de clientes nuevos' en diferentes iniciativas o palancas accionables. Asegúrate de que cada palanca sea clara y medible.

**Entregable:** Árbol de métricas que descompone la métrica objetivo en diferentes iniciativas o palancas accionables.

<details>
<summary>Pistas de conocimiento</summary>

- Considera diferentes áreas del negocio que pueden influir en la activación de clientes nuevos, como marketing, producto, servicio al cliente, etc.

</details>

### Fase 3: Priorización de Iniciativas

**Objetivo:** Priorizar las iniciativas identificadas basándote en su impacto y el esfuerzo requerido para implementarlas.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Prioriza las iniciativas identificadas en la fase anterior basándote en su impacto y el esfuerzo requerido para implementarlas. Asegúrate de que tus supuestos sean explícitos.

**Entregable:** Lista de iniciativas priorizadas con supuestos explícitos sobre su impacto y el esfuerzo requerido para implementarlas.

<details>
<summary>Pistas de conocimiento</summary>

- Considera diferentes metodologías de priorización, como el método de los 2x2 o el método de puntuación.

</details>

## Dimensiones Evaluadas

- **queEs**: ¿Qué es la métrica objetivo 'activación de clientes nuevos' y cómo se descompone en iniciativas accionables?
- **paraQueSirve**: ¿Para qué sirve descomponer la métrica objetivo en iniciativas accionables y priorizarlas?
- **comoSeUsa**: ¿Cómo se usa el árbol de métricas para guiar la toma de decisiones en el negocio?
- **erroresComunes**: ¿Cuáles son los errores comunes al descomponer métricas y priorizar iniciativas?
- **queDecisionesImplica**: ¿Qué decisiones implica la priorización de iniciativas basada en impacto y esfuerzo?

## Criterios de Evaluacion

- Definición clara y detallada de la métrica objetivo 'activación de clientes nuevos'.
- Árbol de métricas que descompone la métrica objetivo en diferentes iniciativas o palancas accionables.
- Lista de iniciativas priorizadas con supuestos explícitos sobre su impacto y el esfuerzo requerido para implementarlas.

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
