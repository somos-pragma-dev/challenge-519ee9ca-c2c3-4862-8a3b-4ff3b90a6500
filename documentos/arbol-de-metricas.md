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