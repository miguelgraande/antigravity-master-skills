---
name: html-security-audit
description: Auditoria completa de seguridad y estabilidad en archivos HTML. Usar cuando el usuario pida "auditar HTML", "security check", "auditoria de estabilidad" o "buscar vulnerabilidades".
---

# HTML Security & Stability Auditor

Audita archivos HTML/JS de forma sistematica buscando crashes, vulnerabilidades de seguridad, problemas de rendimiento y riesgos de dependencias.

## Cuando usar este skill

- El usuario pide auditar un archivo HTML para bugs o vulnerabilidades
- El usuario menciona "security check", "buscar crashes" o "auditar mi codigo"
- El codigo debe funcionar offline o en protocolo file://
- Antes de desplegar o entregar un proyecto web

## Inputs necesarios

1. **Archivo HTML a auditar** (obligatorio)
2. **Tipo de entorno** — file://, localhost, servidor (opcional)

## Workflow

### Fase 1: Discovery (busqueda sistematica)

En orden de severidad:

**1.1 Riesgos de crash (Critico)**
```bash
grep -n ".id]" <archivo>
grep -n ".value" <archivo>
grep -n "getElementById" <archivo>
```

**1.2 Riesgos de seguridad (Alto)**
```bash
grep -n 'innerHTML.*${' <archivo>
grep -n 'innerHTML.*e.message' <archivo>
grep -n 'eval(' <archivo>
```

**1.3 Riesgos de dependencias (Medio)**
```bash
grep -n "cdn.jsdelivr|cdnjs|unpkg" <archivo>
```

**1.4 Riesgos de rendimiento (Bajo)**
```bash
grep -n "mousemove|scroll|resize" <archivo>
```

### Fase 2: Library Guards

Verificar que librerias externas esten protegidas con guards:
```javascript
if (ctx && typeof Chart !== 'undefined') { new Chart(ctx, config); }
```

### Fase 3: Validacion de inputs

Verificar que inputs numericos manejan edge cases correctamente.

### Fase 4: Aplicar fixes

Por cada hallazgo:
1. Documentar linea exacta y fragmento de codigo
2. Crear parche minimo (antes/despues)
3. Anadir comentario `// AUDIT FIX: CRASH-001`

### Fase 5: Generar reporte

Crear `errores/YYYY-MM-DD_auditoria_<archivo>.md` con resumen y fixes.

## Output (formato exacto)

```markdown
# Auditoria de Seguridad y Estabilidad
**Archivo:** <nombre>
**Fecha:** <fecha>

## RESUMEN
| Severidad | Encontrados | Corregidos |
|-----------|-------------|------------|
| Critico   | X           | X          |
| Alto      | Y           | Y          |

## HALLAZGOS
### [CRITICO-001]: <descripcion>
**Linea:** X
**Antes:** `<codigo>`
**Despues:** `<codigo>`
```

## Validacion

- [ ] Fases 1-3 completadas
- [ ] Fixes aplicados con IDs de auditoria
- [ ] Reporte generado
- [ ] No hay nuevos errores de consola tras los fixes
- [ ] La app funciona tras los cambios

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| grep no encuentra nada | El patron no esta | El archivo puede ya estar corregido |
| curl falla | Sin red o URL incorrecta | Usar version especifica conocida |
| Fix rompe funcionalidad | Parche incorrecto | Revertir y revisar logica original |
