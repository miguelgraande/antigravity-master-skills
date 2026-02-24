---
name: frontend-design
description: Crea interfaces frontend distintivas y de produccion con identidad visual propia. Usar cuando se construya o disene una UI web, componentes, paginas o dashboards que deben destacar visualmente.
---

# Frontend Design (Distintivo, Production-Grade)

Crea interfaces memorables con criterio estetico propio. No layouts genericos, no paletas por defecto — diseno con opinion, bien ejecutado.

## Cuando usar este skill

- Se construye o reDisena una interfaz web, componente, pagina o dashboard
- El usuario quiere algo que "no parezca una plantilla"
- Antes de implementar una UI que deba representar una marca o producto
- El resultado debe funcionar en produccion y recordarse visualmente

## Inputs necesarios

1. **Proposito de la interfaz** — que accion debe habilitar? (obligatorio)
2. **Tono dominante** — brutalist, editorial, luxury, retro-futurista, minimal, etc. (obligatorio)
3. **Stack tecnico** — HTML/CSS, React, Vue, etc. (obligatorio)
4. **Restricciones** — branding existente, fuentes, colores de marca (opcional)

## Workflow

### Paso 1: Design Thinking (antes del codigo)

Definir explicitamente:
- **Proposito:** que accion habilita? es persuasiva, funcional, expresiva?
- **Tono:** elegir UN tono dominante (maximo dos)
- **Anchor de diferenciacion:** si se captura sin el logo, como se reconoce?

### Paso 2: Evaluar con DFII

Puntuar del 1-5:

| Dimension | Pregunta |
|---|---|
| Impacto estetico | Que tan distintivo y memorable? |
| Fit con contexto | Encaja con producto, audiencia, proposito? |
| Factibilidad | Se puede construir limpiamente con el stack? |
| Rendimiento | Seguira siendo rapido y accesible? |
| Riesgo consistencia | Se puede mantener en multiples pantallas? |

Formula: `DFII = (Impacto + Fit + Factibilidad + Rendimiento) - Riesgo`
- 12-15: Ejecutar completamente
- 8-11: Proceder con disciplina
- <=7: Repensar direccion

### Paso 3: Implementar

Reglas no negociables:
- **Tipografia:** evitar Inter/Roboto/Arial. 1 fuente expresiva + 1 de cuerpo
- **Color:** CSS variables exclusivamente. 1 tono dominante + 1 acento + 1 neutro
- **Composicion:** romper la cuadricula intencionalmente
- **Motion:** una secuencia de entrada fuerte + hover states significativos
- **Codigo:** semantico, accesible, sin estilos muertos

### Paso 4: Validar

- [ ] Direccion estetica nombrada explicitamente
- [ ] DFII >= 8
- [ ] Un elemento memorable identificado
- [ ] No hay fuentes/colores/layouts genericos
- [ ] Accesible y performante

## Output (formato exacto)

```
## Direccion de diseno
**Estetica:** [nombre]
**DFII:** [puntuacion]
**Inspiracion conceptual:** [descripcion]

## Sistema de diseno
**Fuentes:** [display] + [body]
**Variables CSS clave:** [lista]

## Implementacion
[codigo completo]

## Diferenciacion
"Este diseno evita UI generica haciendo X en lugar de Y."
```

## Antipatrones (fallo inmediato)

- Inter/Roboto/fuentes del sistema
- Gradientes SaaS purpura sobre blanco
- Layouts Tailwind/ShadCN por defecto
- Secciones simetricas y predecibles
- Decoracion sin intencion

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| DFII menor de 8 | Direccion poco ambiciosa | Explorar tonos mas distintivos |
| Diseno parece template | Falta anchor de diferenciacion | Definir elemento memorable y construir desde ahi |
| Codigo no coincide con diseno | Implementacion conservadora | Elevar la ambicion del codigo |
