# Análisis Predictivo - Superstore

Este repositorio contiene un notebook para construir un pipeline de analisis de datos y modelado predictivo sobre el dataset Superstore.

Objetivo principal: predecir la variable Profit.

## Estado actual del notebook

El archivo superstore-analysis.ipynb esta en modo plantilla (estructura de fases lista, celdas de implementacion pendientes).

Esto significa que hoy puedes reproducir correctamente el entorno y abrir/ejecutar el notebook, pero el contenido analitico final aun debe completarse.

## Requisitos

- Python 3.11 o superior
- Sistema operativo: Windows, Linux o macOS
- El dataset local Sample - Superstore.csv (ya incluido en el repo)

Dependencias de Python usadas por el proyecto:

- pandas
- numpy
- matplotlib
- seaborn
- scipy
- scikit-learn
- ipykernel

## Opcion 1 (recomendada): Poetry

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

## Opcion 2: venv + pip (sin Poetry)

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

## Opcion 3: Conda

```bash
conda create -n superstore python=3.11 -y
conda activate superstore
pip install pandas numpy matplotlib seaborn scipy scikit-learn ipykernel notebook
jupyter notebook superstore-analysis.ipynb
```

## Ejecutar en VS Code

1. Abre la carpeta del proyecto en VS Code.
2. Abre superstore-analysis.ipynb.
3. Selecciona el kernel del entorno que configuraste (Poetry, venv o conda).
4. Usa Run All para ejecutar todas las celdas.

## Dataset

- Archivo: Sample - Superstore.csv
- Filas: 9994 transacciones
- Incluye variables de pedido, cliente, geografia, producto y metricas como Sales, Quantity, Discount y Profit.

No se requiere descarga externa del dataset.

## Estructura del repositorio

```text
.
|-- AGENTS.md
|-- pyproject.toml
|-- README.md
|-- Sample - Superstore.csv
`-- superstore-analysis.ipynb
```

## Verificacion rapida de reproduccion

Considera que la reproduccion fue exitosa si:

1. El entorno instala dependencias sin errores.
2. Jupyter o VS Code abre superstore-analysis.ipynb.
3. El kernel corresponde al entorno creado.
4. Las celdas se ejecutan sin errores de importacion.

## Problemas frecuentes

- Error: poetry no se reconoce
	- Solucion: instala Poetry y reinicia la terminal.
- Error: no module named <paquete>
	- Solucion: revisa que el kernel activo sea el mismo entorno donde instalaste dependencias.
- Error de permisos al activar scripts en PowerShell
	- Solucion: ejecuta PowerShell como usuario con permisos y habilita scripts para sesion actual.

## Autor

Brandon Quezada
