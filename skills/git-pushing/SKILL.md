---
name: git-pushing
description: Hace stage, commit convencional y push de cambios git. Usar cuando el usuario quiera guardar y subir cambios, mencione "push", "commit", "subir cambios" o termine una feature.
---

# Git Push Workflow

Hace stage de todos los cambios, crea un commit convencional y hace push al branch remoto.

## Cuando usar este skill

- El usuario pide explicitamente hacer push
- El usuario menciona guardar trabajo en remoto
- Se completa una feature y se quiere compartir
- El usuario dice "subamos esto" o "guarda los cambios"

## Workflow

### Paso 1: Stage de cambios

```bash
git add -A
```

### Paso 2: Commit convencional en espanol

Formato: `<tipo>: <descripcion corta en espanol>`

Tipos: `feat:`, `fix:`, `docs:`, `style:`, `refactor:`, `chore:`

```bash
git commit -m "feat: descripcion del cambio"
```

### Paso 3: Push

```bash
git push -u origin HEAD
```

## Output

```
Stage: X archivos anadidos
Commit: [tipo]: [descripcion]
Push: OK → origin/[branch]
```

## Validacion

- [ ] `git status` limpio tras el push
- [ ] El commit sigue el formato convencional
- [ ] El push llego al remoto sin errores

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| Push rechazado | Branch protegido o divergencia | Hacer pull primero, resolver conflictos |
| Nada que commitear | No hay cambios staged | Verificar que los archivos estan guardados |
| Conflicto de merge | Cambios remotos pendientes | git pull --rebase, resolver, push |
