---
name: brainstorming
description: Genera ideas de calidad con estructura, filtros y seleccion final. Usar cuando el usuario pida "ideas", "variantes", "opciones", "brainstorming" o necesite explorar antes de implementar.
---

# Brainstorming Pro

Genera ideas ejecutables, las filtra con criterio y devuelve una recomendacion clara con primer paso accionable.

## Cuando usar este skill

- El usuario pide ideas, variantes, conceptos, hooks, nombres, formatos o enfoques
- Hay bloqueo creativo o demasiadas opciones y hay que ordenar
- El usuario necesita ideas "buenas para ejecutar", no solo ocurrencias
- Antes de cualquier trabajo creativo: crear features, componentes o funcionalidad nueva
- El usuario dice "brainstorming", "dame opciones", "explora alternativas"

## Inputs necesarios

Si falta alguno, **preguntar antes de avanzar**:

1. **Objetivo exacto** — que se quiere conseguir (obligatorio)
2. **Publico / contexto** — para quien es y donde se usa (obligatorio)
3. **Restricciones** — tiempo, presupuesto, tono, formato, herramientas (obligatorio)
4. **Ejemplos de lo que SI y lo que NO** — preferencias del usuario (opcional)

## Workflow

### Paso 0: Revisar contexto del proyecto

Antes de generar ideas, revisar el estado actual del proyecto:
- Archivos relevantes, estructura, docs y commits recientes
- Funcionalidad existente que pueda afectar o ser reutilizada
- Restricciones tecnicas del stack actual

### Paso 1: Aclarar el encargo

Si faltan inputs, hacer 3-5 preguntas rapidas:
- Una pregunta por mensaje, sin abrumar
- Preferir opciones multiples cuando sea posible

### Paso 2: Generar ideas en 4 tandas

| Tanda | Cantidad | Enfoque |
|---|---|---|
| **A) Rapidas** | 10 ideas | Claras y ejecutables |
| **B) Diferentes** | 5 ideas | Angulos no obvios, creativos |
| **C) Low effort** | 5 ideas | Rapidas de producir, minimo esfuerzo |
| **D) High impact** | 3 ideas | Mas ambiciosas, mas potentes |

Total: 23 ideas como materia prima.

### Paso 3: Filtrar y puntuar

Puntuar cada idea del 1 al 5 en cinco criterios:

| Criterio | Que mide |
|---|---|
| **Impacto** | Cuanto mueve la aguja hacia el objetivo? |
| **Claridad** | Se entiende a la primera? Es facil de explicar? |
| **Novedad** | Aporta algo diferente a lo que ya existe? |
| **Esfuerzo** | Cuanto cuesta implementarlo? (5 = muy facil) |
| **Viabilidad** | Es realista con las restricciones dadas? |

### Paso 4: Entregar TOP 5

- **Idea** — 1 linea
- **Por que funciona** — 2 lineas
- **Primer paso** — 1 linea accionable

## Output (formato exacto)

```
## Ideas
### A) Rapidas (10) / B) Diferentes (5) / C) Low effort (5) / D) High impact (3)

## Puntuacion
| # | Idea | Impacto | Claridad | Novedad | Esfuerzo | Viabilidad | TOTAL |

## TOP 5 Recomendado
### 1. [Nombre]
**Por que funciona:** ...
**Primer paso:** ...
```

## Reglas de calidad

| Regla | Detalle |
|---|---|
| **Nada generico** | Prohibido "mejorar tu productividad". Concretar siempre |
| **YAGNI** | Eliminar ideas que suenen bien pero no aporten valor real |
| **Una pregunta a la vez** | No abrumar al usuario con multiples preguntas simultaneas |

## Validacion

- [ ] Se reviso el contexto del proyecto antes de idear
- [ ] Todos los inputs obligatorios estan cubiertos
- [ ] Se generaron las 4 tandas completas (10+5+5+3 = 23 ideas)
- [ ] Cada idea tiene puntuacion en los 5 criterios
- [ ] TOP 5 incluye idea + por que funciona + primer paso
- [ ] Ninguna idea es generica o no accionable

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| Ideas genericas o vagas | Falta contexto | Volver al Paso 1 y aclarar objetivo |
| Demasiadas ideas similares | Sesgo en una direccion | Forzar tanda B con restriccion explicita |
| Usuario no sabe que quiere | Objetivo no definido | Ofrecer 3 objetivos posibles como opcion multiple |
| Ideas inviables con el stack | No se reviso contexto tecnico | Volver al Paso 0 y revisar proyecto |
