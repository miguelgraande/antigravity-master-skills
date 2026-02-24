---
name: modo-produccion
description: Revisa una app o landing, detecta problemas, aplica correcciones y valida con checklist fijo. Usar cuando el usuario diga "pulir", "revisar antes de ensenar", "modo produccion" o "QA rapido".
---

# Modo Produccion (QA + Fix)

Pasa cualquier app o landing de "funciona a medias" a "lista para ensenar o publicar", con diagnostico priorizado, arreglos minimos y validacion final.

## Cuando usar este skill

- El usuario ya tiene algo generado (landing, app, pagina) y quiere dejarlo presentable
- Algo funciona "a medias": movil raro, imagenes rotas, botones sin accion, espaciados feos
- Antes de ensenarlo a un cliente, grabarlo o publicarlo
- El usuario dice "pulir esto", "revisar", "QA", "modo produccion", "dejalo fino"

## Inputs necesarios

Si falta alguno, **preguntar antes de avanzar**:

1. **Archivo principal** — que archivo revisar (obligatorio)
2. **Objetivo de la revision** — "lista para ensenar" o "lista para publicar" (obligatorio)
3. **Restricciones** — no cambiar branding / no cambiar copy / etc. (opcional)

## Checklist de calidad (orden fijo)

### A) Funciona y se ve
- [ ] Abre la preview / localhost sin errores
- [ ] Imagenes cargan y no hay rutas rotas
- [ ] Tipografias y estilos se aplican correctamente

### B) Responsive (movil primero)
- [ ] Se ve bien en movil (no se corta, no hay scroll horizontal)
- [ ] Botones y textos tienen tamanos legibles
- [ ] Secciones con espaciado coherente

### C) Copy y UX basica
- [ ] Titular claro y coherente con la propuesta
- [ ] CTAs consistentes (mismo verbo, misma intencion)
- [ ] No hay texto placeholder tipo "lorem ipsum"

### D) Accesibilidad minima
- [ ] Contraste razonable en textos
- [ ] Imagenes con `alt`
- [ ] Estructura de headings logica

## Workflow

### Paso 1: Diagnostico rapido
Lista de 5-10 problemas priorizados por gravedad: Critico / Notable / Menor

### Paso 2: Plan de arreglos
Tabla con maximo 8 cambios: que cambio + por que + prioridad.

### Paso 3: Aplicar cambios
- Minimo parche — no rehacer todo
- Respetar branding existente si lo hay

### Paso 4: Validacion
- Confirmar checklist completo (A, B, C, D)
- Verificar que ningun arreglo rompio otra cosa

### Paso 5: Resumen final
- Cambios hechos + resultado + mejoras opcionales pendientes

## Output (formato exacto)

```
## Diagnostico (priorizado)
[CRITICO] 1. ...
[NOTABLE] 2. ...
[MENOR]   3. ...

## Cambios aplicados
- OK [cambio 1]
- OK [cambio 2]

## Resultado
**Estado:** OK para ensenar / OK para publicar
**Notas:** ...
**Opcional:** ...
```

## Reglas de calidad

| Regla | Detalle |
|---|---|
| **Minimo parche** | Corrige lo minimo para ganar calidad rapido |
| **Claridad > Bonito** | Prioriza claridad sobre estetica |
| **Respetar marca** | No cambiar branding si hay skill de marca activo |
| **Maximo 8 cambios** | Priorizar los de mayor impacto |

## Validacion

- [ ] Archivo principal y objetivo identificados
- [ ] Diagnostico con 5-10 problemas priorizados
- [ ] Plan de arreglos con <= 8 cambios justificados
- [ ] Checklist A/B/C/D verificado tras los arreglos
- [ ] Ningun arreglo rompio funcionalidad existente

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| No se puede abrir preview | Ruta incorrecta | Pedir ruta exacta al usuario |
| Arreglo rompe otra seccion | Efectos colaterales | Revertir, aplicar con scope mas acotado |
| Imagenes no cargan | Rutas relativas rotas | Convertir a absolutas |
| Responsive peor tras fix | CSS global alterado | Usar media queries especificas |
| Mas de 10 problemas | App necesita mas trabajo | Priorizar solo criticos, comunicar deuda tecnica |
