# StreamView Analytics

Proyecto académico de análisis descriptivo del catálogo de películas y series, desarrollado para la evaluación del curso ADY1104 de Duoc UC.

## Objetivo

Explorar y comunicar patrones del catálogo a partir de los archivos proporcionados para el caso, utilizando Python/Jupyter para la preparación y el análisis exploratorio, y Power BI para la visualización interactiva.

## Fuentes de datos

Se utilizan exclusivamente los archivos entregados por el curso:

- `netflix_movies_detailed_up_to_2025.csv`
- `netflix_tv_shows_detailed_up_to_2025.csv`

Los archivos originales deben mantenerse en `data/raw/`. Los archivos derivados y las tablas exportadas para Power BI se guardan en `data/processed/`.

## Estructura del proyecto

```text
StreamView-Analytics/
├── data/
│   ├── raw/                 # CSV originales del profesor
│   └── processed/           # Datos preparados y resultados
│       └── resultados/      # CSV resumen para Power BI
├── notebooks/               # Revisión, preparación y análisis exploratorio
├── dashboard/
│   ├── powerbi/             # Archivo .pbix
│   └── d3/                  # Recursos D3.js, si corresponde
├── images/                  # Imágenes y capturas de visualizaciones
├── src/                     # Código auxiliar, si corresponde
├── docs/                    # Informe ejecutivo y documentos
├── requirements.txt
├── .gitignore
└── README.md
```

## Flujo de trabajo reproducible

1. Colocar los dos CSV originales en `data/raw/`.
2. Ejecutar los notebooks en orden:
   - `01_revision_datasets.ipynb`: revisión inicial de estructura, faltantes y duplicados.
   - `02_preparacion_analisis.ipynb`: preparación de datos y creación de variables auxiliares.
   - `03_analisis_exploratorio.ipynb`: análisis descriptivo y exportación de tablas para las visualizaciones.
3. Revisar los CSV generados en `data/processed/` y `data/processed/resultados/`.
4. Abrir el archivo Power BI (`.pbix`) para explorar los dashboards ejecutivo y analítico.

Los nombres de notebooks y carpetas deben coincidir con los archivos que efectivamente se incluyan en la entrega.

## Principales resultados

- Catálogo analítico combinado: **31.991 títulos**.
- Películas: **16.000**.
- Series: **15.991**, tras resolver nueve identificadores duplicados.
- Valoración media válida de películas: **6,31/10**.
- Valoración media válida de series: **7,03/10**.
- La correlación entre popularidad y valoración es muy débil en ambos tipos de contenido.
- El análisis financiero utiliza películas con presupuesto e ingresos mayores que cero; la relación indicada por el caso es `revenue / budget`.

## Criterios y limitaciones

- Los CSV originales se conservan sin modificar; los ajustes se aplican a archivos derivados.
- Para series, los nueve `show_id` duplicados tenían los mismos atributos salvo `popularity`; se promedió esa variable por identificador y se conservó un registro por título.
- Las valoraciones válidas requieren `vote_count > 0` y `vote_average > 0`.
- Los campos faltantes de país, director, reparto o géneros no se deben interpretar como ausencia real de esa característica; pueden etiquetarse como “Sin información”.
- `popularity` es un índice relativo del dataset y **no equivale a reproducciones**.
- La relación `revenue / budget` expresa ingresos en relación con el presupuesto y **no es el ROI neto convencional**.
- La cantidad de registros por año es inusualmente uniforme. No debe interpretarse como una medida del crecimiento real de Netflix.
- Los resultados son descriptivos y no permiten inferir causalidad.

## Herramientas

- Python y Jupyter Notebook
- pandas y herramientas de visualización utilizadas en los notebooks
- Power BI Desktop
- CSV para intercambio de datos

## Entregables

La entrega debe incluir el archivo Power BI (`.pbix`), los notebooks, los datos procesados y sus tablas de resultados, este README y el informe ejecutivo PDF. Añadir cualquier presentación u otro producto solicitado explícitamente en la pauta del curso.

## Autoría y alcance

Proyecto académico elaborado a partir de los datos oficiales proporcionados por el curso. No se incorporan fuentes externas.
