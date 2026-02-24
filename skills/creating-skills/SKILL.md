---
name: creating-skills
description: Crea y valida skills para Antigravity con estructura estandarizada. Usar cuando el usuario pida "crear skill", "nuevo skill", "construir un skill para" o "automatizar un proceso repetitivo".
---

# Creador de Skills

Genera skills predecibles, reutilizables y faciles de mantener, con estructura clara de carpetas y logica que funcione en produccion.

## Cuando usar este skill

- El usuario pide crear un skill o workflow nuevo
- El usuario menciona "crear skill", "nuevo skill", "construir un skill para"
- El usuario quiere automatizar un proceso repetitivo
- El usuario quiere convertir un prompt largo en un procedimiento reutilizable

## Estructura minima obligatoria

Cada skill se crea dentro de:

```
.agent/skills/<nombre-del-skill>/
├── SKILL.md          # Obligatorio: logica y reglas del skill
├── recursos/         # Opcional: guias, plantillas, tokens, ejemplos
├── scripts/          # Opcional: utilidades que el skill ejecuta
└── ejemplos/         # Opcional: implementaciones de referencia
```

> No crear archivos innecesarios. Mantener la estructura lo mas simple posible.
> Si SKILL.md supera 400 lineas, mover el contenido extra a `ADVANCED.md`.

## Reglas de YAML (frontmatter)

El archivo SKILL.md debe empezar siempre con frontmatter YAML:

```yaml
---
name: <nombre-del-skill>
description: <descripcion breve en tercera persona>
---
```

| Regla | Detalle |
|---|---|
| **name** | Minusculas, con guiones. Maximo 40 caracteres. Ej: `auditar-landing` |
| **description** | En espanol, tercera persona. Maximo 220 caracteres. Debe decir que hace y cuando usarlo |
| **Rutas** | Siempre absolutas, siempre con `/` (nunca `\`) |

## Principios de escritura

| Principio | Aplicacion |
|---|---|
| **Claridad sobre longitud** | Pocas reglas, muy claras. Manual de ejecucion, no un blog |
| **No relleno** | Evitar explicaciones tipo tutorial. El agente es inteligente |
| **Separacion de responsabilidades** | Estilo → recurso. Pasos → workflow. Datos → input |
| **Pedir datos cuando falten** | Si un input es critico, preguntar antes de asumir |
| **Salida estandarizada** | Definir exactamente el formato de salida |
| **Limite de 400 lineas** | Si se excede, crear `ADVANCED.md` para el overflow |

### Niveles de libertad

| Nivel | Cuando | Ejemplo |
|---|---|---|
| **Alta libertad** | Brainstorming, ideas, alternativas | Bullet points, opciones abiertas |
| **Media libertad** | Documentos, copys, estructuras | Templates con huecos para rellenar |
| **Baja libertad** | Operaciones fragiles, scripts, deploys | Comandos exactos, sin variacion |

## Workflow

### Paso 1: Recopilar requisitos
- **Proposito:** que logra el skill?
- **Triggers:** 2-3 frases concretas que lo activen
- **Inputs:** que necesita del usuario? que es opcional?
- **Output:** que formato exacto devuelve?

### Paso 2: Validar antes de escribir
- [ ] Entendi el objetivo final
- [ ] Tengo los inputs necesarios (o se cuales pedir)
- [ ] Defini el output exacto
- [ ] No existe ya un skill que haga lo mismo

### Paso 3: Crear el SKILL.md
Secciones obligatorias en orden:
1. Titulo — claro y descriptivo
2. Resumen — una frase de lo que logra
3. Cuando usar este skill — 3+ triggers concretos
4. Inputs necesarios
5. Workflow — pasos numerados
6. Output — formato exacto
7. Validacion — como verificar que funciono
8. Manejo de errores — tabla con errores comunes

### Paso 4: Revisar coherencia
Pasar la checklist de validacion completa.

## Checklist de validacion

- [ ] YAML frontmatter es parseable y completo
- [ ] `name` en minusculas con guiones, <= 40 chars
- [ ] `description` en espanol, tercera persona, <= 220 chars, con triggers
- [ ] Seccion "Cuando usar" tiene 3+ condiciones concretas
- [ ] Todas las rutas son absolutas y usan `/`
- [ ] Lineas totales < 400 (o existe `ADVANCED.md`)
- [ ] Al menos un paso de validacion incluido
- [ ] Tabla de manejo de errores presente
- [ ] Output tiene formato definido explicitamente

## Output (formato exacto)

**Carpeta:** `.agent/skills/<nombre-del-skill>/`

Respuesta con: SKILL.md completo + recursos opcionales si aportan valor real.

## Validacion

Verificar que el archivo generado pasa la checklist completa antes de entregarlo.

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| YAML no se parsea | Frontmatter mal formado | Revisar colones, comillas, guiones |
| Skill no se detecta | Nombre incorrecto o ruta rota | Verificar carpeta en `.agent/skills/` con guiones |
| Triggers no se disparan | Description no incluye frases | Anadir 2-3 frases "Usar cuando..." |
| Rutas rotas | Rutas relativas usadas | Convertir todas a absolutas con `/` |
| Skill demasiado largo | Mas de 400 lineas | Mover contenido secundario a `ADVANCED.md` |
| Output inconsistente | No se definio formato | Anadir seccion "Output" con formato exacto |
