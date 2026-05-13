# Análisis Predictivo - Superstore

Este repositorio contiene un pipeline completo de análisis de datos y modelado predictivo sobre el dataset **Superstore**. El objetivo principal es predecir la variable **Profit** a partir de las variables de transacción.

## Estado actual

El proyecto está **completo** y ejecutable. El notebook `superstore-analysis.ipynb` contiene las 3 fases implementadas y ejecutadas:

- **Fase 1 — Data Wrangling:** carga, limpieza, ingeniería de features, codificación y exportación del dataset limpio.
- **Fase 2 — EDA:** análisis univariado, bivariado, temporal, segmentado y detección de outliers con visualizaciones.
- **Fase 3 — Modelado Predictivo:** entrenamiento y comparación de Linear Regression, Ridge y Random Forest, con validación cruzada, ajuste de hiperparámetros e interpretación de resultados.

## Requisitos

- Python 3.11 o superior
- Sistema operativo: Windows, Linux o macOS
- El dataset local `Sample - Superstore.csv` ya está incluido en el repositorio

Dependencias de Python usadas por el proyecto:

- pandas
- numpy
- matplotlib
- seaborn
- scipy
- scikit-learn
- ipykernel

## Opción 1 (recomendada): Poetry

1. Clona el repositorio y entra a la carpeta del proyecto.
2. Instala dependencias.
3. Ejecuta Jupyter con el entorno del proyecto.

```bash
poetry install
poetry run jupyter notebook superstore-analysis.ipynb
```

Si prefieres JupyterLab:

```bash
poetry run jupyter lab
```

## Opción 2: venv + pip (sin Poetry)

1. Crea y activa un entorno virtual.
2. Instala dependencias equivalentes.
3. Abre el notebook.

Windows (PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install pandas numpy matplotlib seaborn scipy scikit-learn ipykernel notebook
jupyter notebook superstore-analysis.ipynb
```

Linux/macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install pandas numpy matplotlib seaborn scipy scikit-learn ipykernel notebook
jupyter notebook superstore-analysis.ipynb
```

## Opción 3: Conda

```bash
conda create -n superstore python=3.11 -y
conda activate superstore
pip install pandas numpy matplotlib seaborn scipy scikit-learn ipykernel notebook
jupyter notebook superstore-analysis.ipynb
```

## Ejecutar en VS Code

1. Abre la carpeta del proyecto en VS Code.
2. Abre `superstore-analysis.ipynb`.
3. Selecciona el kernel del entorno que configuraste (Poetry, venv o conda).
4. Usa **Run All** para ejecutar todas las celdas.

## Dataset

- **Archivo original:** `Sample - Superstore.csv`
- **Archivo limpio:** `superstore_clean.csv`
- **Filas:** 9994 transacciones retail
- **Columnas:** 21 originales + features engineered (temporales, de negocio, logs, outliers)

Incluye variables de pedido, cliente, geografía, producto y métricas como Sales, Quantity, Discount y Profit. No se requiere descarga externa.

## Hallazgos principales

- **Categoría más rentable:** Technology ($145,455 total) vs Furniture ($18,451).
- **Región más rentable:** West ($108,418) vs Central ($39,706).
- **Impacto del descuento:** profit promedio cae drásticamente con descuentos altos (High: -$89.44, Medium: -$109.53).
- **Mejor mes:** Diciembre ($43,369 profit total); **peor mes:** Enero ($9,134).
- **Outliers:** 2,120 transacciones (21.2%) marcadas como outliers en Sales o Profit.
- **Modelo ganador:** Random Forest con MAE de ~$25.79, reduciendo el error baseline (~$67) en más de 60%.
- **Features más importantes:** Sales, LogSales y Discount concentran el ~88% de la importancia predictiva.

## Estructura del repositorio

```text
.
|-- AGENTS.md                          # Guía para agentes de código
|-- pyproject.toml                     # Configuración de Poetry
|-- poetry.lock                        # Lock de dependencias
|-- README.md                          # Este archivo
|-- .gitignore                         # Archivos ignorados por git
|-- Sample - Superstore.csv            # Dataset original (9994 filas)
|-- superstore_clean.csv               # Dataset limpio con features (9994 filas, 46 cols)
|-- superstore-analysis.ipynb          # Notebook principal (pipeline completo)
|-- .agents/
|   `-- skills/
|       |-- data-preparation.md        # Skill: Fase 1
|       |-- exploratory-analysis.md    # Skill: Fase 2
|       `-- predictive-modeling.md     # Skill: Fase 3
|-- .venv/                             # Entorno virtual ( Poetry / venv )
```

## Verificación rápida de reproducción

Considera que la reproducción fue exitosa si:

1. El entorno instala dependencias sin errores.
2. Jupyter o VS Code abre `superstore-analysis.ipynb`.
3. El kernel corresponde al entorno creado.
4. Las celdas se ejecutan sin errores de importación.
5. Se genera `superstore_clean.csv` tras ejecutar la Fase 1.

## Problemas frecuentes

- **Error: poetry no se reconoce**
  - Solución: instala Poetry y reinicia la terminal.
- **Error: no module named `<paquete>`**
  - Solución: revisa que el kernel activo sea el mismo entorno donde instalaste dependencias.
- **Error de permisos al activar scripts en PowerShell**
  - Solución: ejecuta PowerShell como usuario con permisos y habilita scripts para sesión actual.

## Autor

Brandon Quezada
