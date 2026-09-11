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