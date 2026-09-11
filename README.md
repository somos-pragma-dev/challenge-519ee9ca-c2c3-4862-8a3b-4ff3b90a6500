# Diseño y priorización de iniciativas para aumentar la activación de clientes nuevos

El equipo de Business Consulting necesita diseñar un árbol de métricas que permita descomponer la métrica objetivo de activación de clientes nuevos en palancas accionables. Posteriormente, se debe priorizar estas iniciativas basándose en su impacto y esfuerzo, con supuestos explícitos.

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

### Fase 1: Definición del árbol de métricas

**Objetivo:** Crear un árbol de métricas que descomponga la activación de clientes nuevos en palancas accionables.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Identificar las métricas clave que influyen en la activación de clientes nuevos.
- Descomponer cada métrica en submétricas y palancas accionables.
- Documentar el árbol de métricas con claridad y detalle.

**Entregable:** Árbol de métricas documentado.

<details>
<summary>Pistas de conocimiento</summary>

- Considerar métricas relacionadas con el engagement, la conversión y la retención.
- Incluir supuestos y fuentes de datos para cada métrica.

</details>

### Fase 2: Priorización de iniciativas

**Objetivo:** Priorizar las iniciativas identificadas en el árbol de métricas basándose en su impacto y esfuerzo.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Evaluar cada iniciativa en términos de impacto y esfuerzo.
- Documentar los supuestos y criterios utilizados para la priorización.
- Crear una matriz de priorización con las iniciativas ordenadas.

**Entregable:** Matriz de priorización de iniciativas.

<details>
<summary>Pistas de conocimiento</summary>

- Utilizar una escala de 1 a 5 para evaluar impacto y esfuerzo.
- Incluir supuestos explícitos para cada iniciativa.

</details>

### Fase 3: Revisión y ajustes

**Objetivo:** Revisar y ajustar el árbol de métricas y la priorización de iniciativas basándote en feedback y nuevos datos.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Recopilar feedback de stakeholders y datos adicionales.
- Ajustar el árbol de métricas y la matriz de priorización si es necesario.
- Documentar los cambios y las razones detrás de ellos.

**Entregable:** Árbol de métricas y matriz de priorización ajustados.

<details>
<summary>Pistas de conocimiento</summary>

- Considerar feedback de diferentes fuentes para asegurar una visión completa.
- Documentar cualquier cambio significativo y las razones detrás de él.

</details>

## Dimensiones Evaluadas

- **queEs**: ¿Qué es un árbol de métricas y por qué es importante para la priorización de iniciativas?
- **paraQueSirve**: ¿Cómo se utiliza un árbol de métricas para descomponer y entender mejor una métrica objetivo?
- **comoSeUsa**: ¿Cómo se aplica la priorización de iniciativas en un contexto real de negocio?
- **erroresComunes**: ¿Cuáles son los errores comunes al crear un árbol de métricas y priorizar iniciativas?
- **queDecisionesImplica**: ¿Qué decisiones implica la priorización de iniciativas y cómo se toman?

## Criterios de Evaluacion

- Crear un árbol de métricas que descomponga la activación de clientes nuevos en palancas accionables.
- Priorizar las iniciativas identificadas basándose en impacto y esfuerzo con supuestos explícitos.
- Revisar y ajustar el árbol de métricas y la priorización de iniciativas basándose en feedback y nuevos datos.

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
