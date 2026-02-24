---
name: doc-to-app
description: Convierte un documento (PDF/texto) en una mini-app web interactiva navegable. Usar cuando el usuario diga "convierte este doc", "hazme una app de esto", "doc to app" o pase un PDF/texto para visualizar.
---

# Doc-to-App (Documento a Mini-App)

Transforma cualquier documento (PDF, texto, notas) en una mini web navegable con buscador, filtros y secciones claras, lista para abrir en preview o compartir.

## Cuando usar este skill

- El usuario pasa un PDF, texto o notas y quiere transformarlo en algo navegable
- El usuario dice "convierte esto en una app", "hazme una mini web", "doc to app"
- Cuando hay informacion densa que necesita buscador, filtros o navegacion
- Antes de ensenar o compartir contenido en formato documento

## Inputs necesarios

Si falta alguno, **preguntar antes de avanzar**:

1. **Fuente** — PDF o texto pegado (obligatorio)
2. **Tipo de app** — guia, catalogo, checklist, itinerario, dashboard, etc. (obligatorio)
3. **Prioridad** — "mas visual" o "mas practica" (obligatorio)
4. **Idioma y estilo** — por defecto espanol (opcional)

## Estructura de salida (crear siempre)

Crear una carpeta nueva:

```
miniapp_<tema>_<YYYYMMDD_HHMM>/
├── index.html      # La app completa (sin frameworks)
├── data.json       # Datos estructurados extraidos del documento
└── README.txt      # Como abrirla y que incluye
```

> **No sobrescribir nada.** Cada ejecucion crea una carpeta nueva.

## Funcionalidades minimas de la app

| Funcionalidad | Detalle |
|---|---|
| **Buscador** | Por texto, filtrado en tiempo real |
| **Filtros** | Por categorias/etiquetas |
| **Navegacion** | Indice arriba o lateral por secciones |
| **Responsive** | Diseno limpio, legible, movil primero |
| **Botones utiles** | Copiar, marcar como hecho, expandir/contraer |

La app usa HTML + CSS + JS vanilla. **Sin frameworks.**

## Workflow

### Paso 1: Leer y extraer estructura
Identificar: secciones, listas, tablas, puntos clave, jerarquias.

### Paso 2: Generar data.json
Convertir contenido a JSON ordenado: secciones → items → propiedades.

### Paso 3: Generar index.html
- Lee de data.json
- Implementa funcionalidades minimas
- Diseno premium: tipografia limpia, espaciado generoso
- **Responsive obligatorio**

### Paso 4: Validacion
- [ ] Se ve bien en escritorio y movil
- [ ] Buscador funciona
- [ ] Filtros filtran correctamente
- [ ] No hay contenido roto ni secciones vacias

### Paso 5: Entrega
Informar carpeta creada + archivo a abrir + resumen de secciones.

## Output (formato exacto)

```
## Carpeta creada
`miniapp_<tema>_<YYYYMMDD_HHMM>/`

## Abre
`miniapp_<tema>_<YYYYMMDD_HHMM>/index.html`

## Contenido incluido
- **Secciones:** [lista]
- **Total items:** [numero]
- **Funcionalidades:** Buscador, filtros por [X], navegacion por secciones
```

## Reglas de calidad

| Regla | Detalle |
|---|---|
| **No solo texto** | Crear siempre archivos, nunca texto plano |
| **No sobrescribir** | Cada ejecucion crea carpeta nueva con timestamp |
| **Movil primero** | Obligatorio |
| **Sin frameworks** | HTML + CSS + JS vanilla |
| **Diseno premium** | No hacer algo feo y basico |

## Validacion

- [ ] Carpeta creada con 3 archivos (index.html, data.json, README.txt)
- [ ] data.json tiene toda la informacion del original
- [ ] index.html lee de data.json y renderiza bien
- [ ] Buscador y filtros funcionan
- [ ] Se ve bien en movil
- [ ] README.txt explica como abrir

## Manejo de errores

| Error | Causa | Resolucion |
|---|---|---|
| PDF no se puede leer | Formato protegido | Pedir al usuario que pegue el texto |
| Contenido sin estructura | Documento sin secciones | Proponer estructura antes de generar |
| App no carga | Rutas rotas o JS con error | Verificar rutas y consola |
| Se ve mal en movil | CSS no responsive | Usar media queries y unidades relativas |
