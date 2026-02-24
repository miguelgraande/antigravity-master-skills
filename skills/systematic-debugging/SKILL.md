---
name: systematic-debugging
description: Debugging sistematico en 4 fases. Usar cuando hay un bug, fallo en tests o comportamiento inesperado — siempre causa raiz antes de proponer cualquier fix.
---

# Systematic Debugging

Siempre encontrar la causa raiz antes de intentar cualquier fix. Los parches rapidos enmascaran el problema real.

## Cuando usar este skill

- Cualquier bug, fallo en tests o comportamiento inesperado
- Especialmente bajo presion de tiempo
- Cuando ya se intentaron multiples fixes sin exito
- Cuando no se entiende completamente el problema

## La Ley de Hierro

```
NINGUN FIX SIN INVESTIGACION DE CAUSA RAIZ PRIMERO
```

Si no has completado la Fase 1, no puedes proponer fixes.

## Workflow: Las 4 Fases

### Fase 1: Investigacion de Causa Raiz

Antes de intentar CUALQUIER fix:

1. **Leer los mensajes de error completos** — contienen la solucion exacta con frecuencia
2. **Reproducir de forma consistente** — si no es reproducible, recopilar mas datos
3. **Revisar cambios recientes** — git diff, commits recientes, nuevas dependencias
4. **Trazar el flujo de datos** — de donde viene el valor incorrecto

### Fase 2: Analisis de Patrones

1. Encontrar ejemplos que funcionan en el mismo codebase
2. Comparar con referencias: leer COMPLETAMENTE, no hacer skimming
3. Identificar diferencias entre lo que funciona y lo que no

### Fase 3: Hipotesis y Testing

1. Formular UNA sola hipotesis clara
2. Hacer el cambio MAS PEQUENO posible para testearla
3. Una variable a la vez — no multiples cambios simultaneos
4. Si no funciona: nueva hipotesis, NO acumular mas fixes

### Fase 4: Implementacion

1. Crear test que falle primero (caso minimo reproducible)
2. Implementar UN solo fix — la causa raiz identificada
3. Verificar: el test pasa? no rompio otros tests?
4. Si 3+ fixes fallaron: cuestionar la arquitectura antes de continuar

## Output

```
## Diagnostico
**Causa raiz identificada:** [descripcion clara]
**Evidencia:** [que prueba que esta es la causa]

## Fix aplicado
**Cambio:** [descripcion del cambio minimo]
**Resultado:** [pasa/falla + detalles]
```

## Senales de alarma — PARAR y seguir el proceso

- "Fix rapido por ahora, investigo despues" → PARAR
- "Probablemente es X, dejame arreglarlo" → PARAR
- "Multiples cambios a la vez" → PARAR
- "Un intento mas" (cuando ya se fallaron 2+) → PARAR y cuestionar arquitectura

## Validacion

- [ ] Se leyeron los mensajes de error completos
- [ ] Se reprodujo el bug de forma consistente
- [ ] Se identifico la causa raiz (no el sintoma)
- [ ] El fix es el cambio minimo necesario
- [ ] No se rompieron otros tests o funcionalidad

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| No reproducible | Condicion de carrera | Anadir logging, probar en distintos entornos |
| Demasiados fixes fallados | Problema arquitectural | Parar, discutir arquitectura |
| Causa raiz poco clara | Evidencia insuficiente | Anadir mas puntos de diagnostico |
| Fix crea nuevos bugs | Efectos colaterales | Revertir, analizar dependencias |
