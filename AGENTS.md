# AGENTS.md

Instrucciones para el agente de IA que abra este repositorio (Claude Code, Cursor, Codex, Copilot, Gemini). Se cargan solas: no hay que pegar nada en ningun chat.

## Que es este repositorio

Es el codigo base de un reto de aprendizaje de Pragma: **Diseño y priorización de iniciativas para aumentar la activación de clientes nuevos**.

| | |
|---|---|
| Tema | Árbol de métricas y priorización de iniciativas |
| Nivel | advanced-l2 |
| Chapter | Business Consulting |
| Especialidad | Business Consulting |
| Stack | Markdown / Árbol de Métricas con Priorización por Impacto/Esfuerzo |
| Patron arquitectonico | Estructura de Trabajo Basada en Evidencia con Análisis Cuantitativo y Cualitativo |
| Tiempo estimado | 10 horas |

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

- **Fase 1 — Identificación de métricas clave**: Lista de métricas clave con definiciones y relevancia.
- **Fase 2 — Descomposición de métricas en palancas accionables**: Desglose de métricas en palancas accionables con descripciones.
- **Fase 3 — Priorización de iniciativas**: Lista de iniciativas priorizadas con supuestos explícitos.
- **Fase 4 — Diseño del árbol de métricas**: Árbol de métricas diseñado.

Distincion operativa:

- **Arreglar** (si): import faltante, tipo que no existe, dependencia sin declarar, error de sintaxis, archivo referenciado que no existe.
- **No tocar** (no): logica de negocio incompleta, validaciones ausentes, secretos hardcodeados, APIs deprecadas que funcionan, concurrencia insegura, patrones mejorables. Eso es lo que la persona tiene que encontrar.

## Lo que falta y tenes que completar

### 1. Archivos que la arquitectura declara (1 de 9)

La propuesta arquitectonica del reto los lista y no llegaron al repo. Crealos con implementacion real, respetando la capa en la que viven:

- [ ] `visualizacion/matriz_priorizacion.png`

### Presentes (8)

- `diagnostico/diagnostico.md`
- `diagnostico/metricas_clave.csv`
- `analisis/arbol-de-metricas.md`
- `analisis/hipotesis.csv`
- `analisis/modelo.csv`
- `priorizacion/plan-de-accion.md`
- `priorizacion/recomendacion.md`
- `visualizacion/arbol_metricas.png`

### Capas del patron declarado

Cada una tiene que existir como directorio real con al menos un archivo. Codigo plano en la raiz no satisface el patron.

- `diagnostico`
- `analisis`
- `priorizacion`
- `visualizacion`

## Verificacion

```bash
python3 -c "import csv,glob; [list(csv.DictReader(open(f))) for f in glob.glob('*.csv')]"
```

Ese comando pasando es la definicion de "terminado" para vos.

## Convenciones que tenes que respetar

- Un solo ecosistema: no declares librerias de otro lenguaje ni mezcles gestores de paquetes.
- Toda libreria que uses tiene que estar declarada en el manifiesto de dependencias.
- Todo import declarado tiene que usarse; todo tipo usado tiene que existir o venir de una dependencia declarada.
- El patron es **Estructura de Trabajo Basada en Evidencia con Análisis Cuantitativo y Cualitativo**: los contratos (interfaces, puertos) los define la capa interna y los implementa la externa, nunca al revés.
- Los archivos que crees llevan implementacion real, no stubs: sin `TODO`, sin cuerpos vacios, sin `// getters y setters`.

## Contexto del candidato

Sirve para calibrar el nivel del codigo, no para resolver las fases.

- Perfil: Chapter Business Consulting, Especialidad Business Consultant, Tecnología Metricas de Negocio, Advanced
- Brecha que el reto ataca: Descompone la metrica objetivo en palancas accionables y prioriza por impacto y esfuerzo con supuestos explicitos
- Mision: Aumentar la activacion de clientes nuevos

---

*Generado por Challenge Generator — Pragma. `README.md` tiene el enunciado completo del reto para la persona. `PROMPT_MEJORA.md` es la variante para pegar en un chat, si se prefiere ese flujo.*
