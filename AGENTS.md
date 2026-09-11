# AGENTS.md

Instrucciones para el agente de IA que abra este repositorio (Claude Code, Cursor, Codex, Copilot, Gemini). Se cargan solas: no hay que pegar nada en ningun chat.

## Que es este repositorio

Es el codigo base de un reto de aprendizaje de Pragma: **Diseño y Priorización de Árbol de Métricas**.

| | |
|---|---|
| Tema | Árbol de métricas y priorización de iniciativas |
| Nivel | advanced-l2 |
| Chapter | Business Consulting |
| Especialidad | Business Consulting |
| Stack | Markdown + CSV / Árbol de Métricas + Priorización por Impacto/Esfuerzo |
| Patron arquitectonico | Estructura de Consultoría de Negocio con Análisis Cuantitativo |
| Tiempo estimado | 8 horas |

## Tu tarea

Dejar este conjunto de artefactos en estado **verificable**: que el comando de verificacion corra sin errores. Escribi los archivos en disco, en este repositorio. No generes ZIPs ni archivos adjuntos.

En orden:

1. Corre `python3 -c "import csv,glob; [list(csv.DictReader(open(f))) for f in glob.glob('*.csv')]"` y mira que falla.
2. Completa lo que falte de la lista de abajo: manifiesto de dependencias, punto de entrada, capa de interfaz y las capas del patron declarado.
3. Arregla SOLO los errores que impiden compilar o arrancar.
4. Volve a correr `python3 -c "import csv,glob; [list(csv.DictReader(open(f))) for f in glob.glob('*.csv')]"` hasta que pase.
5. Pará ahí.

## Regla dura: las fases son trabajo del humano

**PROHIBIDO implementar los entregables de las fases.** El valor del reto esta en que la persona los resuelva. Tu trabajo es que tenga un proyecto que arranca; el hueco pedagogico se queda como esta.

No resuelvas nada de esto:

- **Fase 1 — Definición de la Métrica Objetivo**: Descripción clara y detallada de la métrica objetivo 'activación de clientes nuevos'.
- **Fase 2 — Descomposición de la Métrica en Palancas Accionables**: Árbol de métricas que descompone la métrica objetivo en diferentes iniciativas o palancas accionables.
- **Fase 3 — Priorización de Iniciativas**: Lista de iniciativas priorizadas con supuestos explícitos sobre su impacto y el esfuerzo requerido para implementarlas.

Distincion operativa:

- **Arreglar** (si): import faltante, tipo que no existe, dependencia sin declarar, error de sintaxis, archivo referenciado que no existe.
- **No tocar** (no): logica de negocio incompleta, validaciones ausentes, secretos hardcodeados, APIs deprecadas que funcionan, concurrencia insegura, patrones mejorables. Eso es lo que la persona tiene que encontrar.

## Lo que falta y tenes que completar

No se detectaron huecos: estan los archivos declarados, el boilerplate del stack y ninguna referencia quedo colgando. Igual corre el comando de verificacion — que los archivos existan no garantiza que compilen.

### Presentes (6)

- `datos/hipotesis.csv`
- `datos/modelo.csv`
- `documentos/diagnostico.md`
- `documentos/arbol-de-metricas.md`
- `documentos/plan-de-accion.md`
- `documentos/recomendacion.md`

### Capas del patron declarado

Cada una tiene que existir como directorio real con al menos un archivo. Codigo plano en la raiz no satisface el patron.

- `documentos`
- `datos`

## Verificacion

```bash
python3 -c "import csv,glob; [list(csv.DictReader(open(f))) for f in glob.glob('*.csv')]"
```

Ese comando pasando es la definicion de "terminado" para vos.

## Convenciones que tenes que respetar

- Un solo ecosistema: no declares librerias de otro lenguaje ni mezcles gestores de paquetes.
- Toda libreria que uses tiene que estar declarada en el manifiesto de dependencias.
- Todo import declarado tiene que usarse; todo tipo usado tiene que existir o venir de una dependencia declarada.
- El patron es **Estructura de Consultoría de Negocio con Análisis Cuantitativo**: los contratos (interfaces, puertos) los define la capa interna y los implementa la externa, nunca al revés.
- Los archivos que crees llevan implementacion real, no stubs: sin `TODO`, sin cuerpos vacios, sin `// getters y setters`.

## Contexto del candidato

Sirve para calibrar el nivel del codigo, no para resolver las fases.

- Perfil: Chapter Business Consulting, Especialidad Business Consultant, Tecnología Metricas de Negocio, Advanced
- Brecha que el reto ataca: Descompone la metrica objetivo en palancas accionables y prioriza por impacto y esfuerzo con supuestos explicitos
- Mision: Aumentar la activacion de clientes nuevos

---

*Generado por Challenge Generator — Pragma. `README.md` tiene el enunciado completo del reto para la persona. `PROMPT_MEJORA.md` es la variante para pegar en un chat, si se prefiere ese flujo.*
