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