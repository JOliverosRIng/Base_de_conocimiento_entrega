# Base de Conocimiento — Encoder Multilingual

Proyecto de búsqueda semántica sobre una base de conocimiento. Recupera los
fragmentos (`chunks`) más relevantes para un conjunto de consultas mediante
un índice FAISS y el encoder `intfloat/multilingual-e5-base`.

## Requisitos

- Python 3.9 o superior.

## Instalación

Crea un entorno virtual e instala las dependencias:

```bash
python -m venv venv
source venv/bin/activate        # Linux / macOS
# venv\Scripts\activate         # Windows

pip install -r entrega/requirements.txt
```

Dependencias instaladas:

| Paquete              | Uso                                  |
|----------------------|--------------------------------------|
| `faiss-cpu`          | Índice FAISS y búsqueda de vectores. |
| `numpy`              | Manejo de arrays y embeddings.        |
| `sentence-transformers` | Carga del encoder `multilingual-e5-base`. |

## Descargar la base vectorial

El script necesita dos archivos que **no están en el repositorio**:

| Archivo          | Descripción                                                   |
|------------------|---------------------------------------------------------------|
| `index.faiss`    | Índice FAISS con los vectores de los documentos.              |
| `metadata.jsonl` | Metadatos de los chunks (cada línea corresponde a un vector). |

> **Importante:** el archivo debe llamarse exactamente `index.faiss`
> (no `indice.faiss`), ya que es el nombre que referencia `generador.py`.

Pasos:

1. Abre el enlace de Google Drive:

   https://drive.google.com/drive/folders/1c3tGyRZD3_xiCGm_7IodyY2H409THRyR

2. Selecciona `index.faiss` y `metadata.jsonl`, haz clic derecho y elige
   **Descargar**.

3. Coloca ambos archivos en la carpeta:

   ```
   entrega/base_vectorial/encoder_multilingual/
   ```

La carpeta debe quedar así:

```
entrega/base_vectorial/encoder_multilingual/
├── index.faiss
└── metadata.jsonl
```

## Ejecutar el generador

El script `generador.py` lee las consultas de `entrega/consultas.jsonl`,
realiza la búsqueda en FAISS y escribe los resultados en
`entrega/resultados.jsonl`.

Desde la raíz del proyecto:

```bash
python entrega/generador.py
```

Al terminar, los resultados quedan en `entrega/resultados.jsonl`.

### Nota sobre las rutas

`generador.py` define rutas relativas con el prefijo
`scripts/preprocessing/entrega/`. Si al ejecutarlo obtienes un error de
archivo no encontrado (`FileNotFoundError`), ajusta las constantes al inicio
del bloque de ejecución (líneas ~198-202) a la estructura de tu equipo, por
ejemplo:

```python
RUTA_INDEX     = 'entrega/base_vectorial/encoder_multilingual/index.faiss'
RUTA_METADATA  = 'entrega/base_vectorial/encoder_multilingual/metadata.jsonl'
RUTA_CONSULTAS = 'entrega/consultas.jsonl'
RUTA_RESULTADOS = 'entrega/resultados.jsonl'
```

## Estructura del proyecto

```
.
├── README.md
└── entrega/
    ├── generador.py
    ├── consultas.jsonl
    ├── resultados.jsonl
    ├── requirements.txt
    ├── Informe Tecnico.pdf
    └── base_vectorial/
        └── encoder_multilingual/
            ├── index.faiss
            └── metadata.jsonl
```
