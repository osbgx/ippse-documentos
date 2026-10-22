# IPPSE — Documentos e Informes

Repositorio público de contenido del **Instituto de Profesionales Paraguayos del Sector Eléctrico (IPPSE)**.

Aquí vive el contenido editable del sitio: los informes técnicos y las publicaciones.
El sitio web se genera automáticamente a partir de estos archivos, así que **publicar un
informe nuevo no requiere tocar el código del sitio**: se agrega un archivo `.md` y listo.

---

## Estructura

```
ippse-documentos/
├── README.md                      ← este archivo
├── contenido/
│   └── publicaciones/             ← un archivo .md por informe o publicación
│       ├── informe-2-26.md
│       └── ...
├── imagenes/                      ← imágenes de los informes
│   └── informe-2-26/              ← una carpeta por publicación (mismo id que el .md)
│       └── portada.png
└── esquema/
    └── publicacion.schema.json    ← campos válidos del frontmatter
```

## Cómo publicar un informe nuevo

1. Creá un archivo en `contenido/publicaciones/`. El **nombre del archivo es el `id`** de la
   publicación: usá minúsculas, sin tildes y con guiones (`balance-oferta-demanda-2026.md`).
2. Escribí la cabecera YAML (frontmatter) con los datos del informe y, debajo, el contenido
   en Markdown.
3. Si el informe lleva imágenes, ponélas en `imagenes/<id>/` y referencialas con rutas
   relativas (`../imagenes/<id>/portada.png`).
4. Subí los cambios. El sitio se regenera solo.

Los nombres de archivo que empiezan con `_` o `.` se ignoran (sirven para borradores).

## Formato del archivo

```markdown
---
titulo: Balance oferta-demanda del Sistema Interconectado Nacional 2026–2030
fecha: 2026-10-01
categoria: diagnostico
autor: Comité Técnico Asesor
extracto: Actualización del balance entre oferta y demanda de potencia y energía del SIN.
lectura: 32
estado: publicado
---

## Resumen ejecutivo

El presente informe analiza...

## Metodología

...
```

### Campos del frontmatter

| Campo       | Obligatorio | Tipo   | Descripción |
|-------------|-------------|--------|-------------|
| `titulo`    | Sí          | texto  | Título completo del informe. |
| `fecha`     | Sí          | fecha  | `AAAA-MM-DD` o `AAAA-MM`. Ordena el listado. |
| `categoria` | Sí          | opción | `diagnostico`, `propuesta` u `opinion`. |
| `autor`     | Sí          | texto  | Autor o comité responsable. |
| `extracto`  | Sí          | texto  | Resumen de 1–2 frases para la tarjeta. |
| `lectura`   | No          | número | Minutos de lectura estimados. |
| `estado`    | No          | opción | `publicado` (por defecto) o `proximamente`. |
| `pdf`       | No          | texto  | Ruta al PDF oficial, si existe. |
| `portada`   | No          | texto  | Imagen de portada, relativa a `imagenes/<id>/`. |
| `etiquetas` | No          | lista  | Palabras clave para búsqueda y SEO. |
| `destacado` | No          | bool   | `true` para resaltarlo en la portada del sitio. |

El esquema completo y validable está en [`esquema/publicacion.schema.json`](esquema/publicacion.schema.json).

## Imágenes

Cada publicación puede tener su propia carpeta en `imagenes/`:

```
imagenes/
└── informe-2-26/
    ├── portada.png
    └── figura-1-demanda.png
```

Se referencian desde el Markdown con rutas relativas:

```markdown
![Proyección de demanda](../imagenes/informe-2-26/figura-1-demanda.png)
```

Formatos recomendados: **PNG** para gráficos y **JPG/WebP** para fotografías. Evitá archivos
de más de 1–2 MB; conviene comprimirlos antes de subirlos.

## Convenciones

- **Idioma:** español (Paraguay). UTF-8.
- **Fechas:** siempre ISO (`AAAA-MM-DD`). Sin comillas en el YAML.
- **Un solo `#` (H1)** por documento, o ninguno: el sitio usa el `titulo` del frontmatter.
- **Secciones:** usá `##` para las secciones principales; el sitio genera el índice a partir de ellas.
- **Enlaces internos** entre informes: `[ver el informe anterior](./informe-2-26.md)`.
- **Mojibake:** guardá los archivos en UTF-8 sin BOM para que las tildes y `–` se vean bien.

## Licencia y uso

El contenido es propiedad del IPPSE y se publica para consulta y difusión. Citá la fuente
como *IPPSE — Instituto de Profesionales Paraguayos del Sector Eléctrico*.
