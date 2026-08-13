# Base de Conocimiento — CODEFEST AD ASTRA 2026 (Etapa 1)

Pipeline de preprocesamiento y segmentación (chunking) del corpus documental
del reto, orientado a la construcción de una base de conocimiento vectorial
para recuperación de información en el dominio aeroespacial.

## Descripción

El sistema convierte documentos crudos de múltiples formatos en fragmentos
(chunks) limpios y uniformes, listos para ser vectorizados e indexados.
Sigue un patrón de dos capas: lectores por fuente (extracción) + un
procesador de texto reutilizable (limpieza, segmentación y validación).

## Formatos soportados

- **PDF** — extracción de texto con OCR de respaldo (Tesseract)
- **JSON** — extracción de campos de texto y aplanado de estructura
- **CSV / XLSX** — cada fila como unidad, con control de tokens
- **PBF** — mapas vectoriales (Mapbox Vector Tiles) a texto
- **Imágenes** — OCR con filtro de confianza
- **TXT** — texto plano

## Características

- Segmentación por oraciones con ventana deslizante (250 palabras / 250
  tokens) y solapamiento configurable, sin cortar oraciones.
- Limpieza de ruido (marcadores de página, boilerplate, puntos de relleno).
- Detección automática de idioma (es / en / pt).
- Identificadores reproducibles (doc_id por hash de ruta relativa).
- Validación de integridad y recuperación de texto perdido entre chunks.
- Procesamiento por lotes con paralelismo y reanudación (resumen + changelog).

## Requisitos

- Python 3.12
- Tesseract OCR (binario del sistema)
- Ver `requirements.txt` para las dependencias de Python

## Uso

Ejecutar el notebook orquestador (`scripts/preprocessing/orquestador.ipynb`),
que recorre el corpus, delega cada archivo en su preprocesador y consolida
los chunks en `output/metadata.json`.
