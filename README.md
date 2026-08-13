# Encoder Multilingual

Esta carpeta debe contener la base vectorial (índice FAISS) y los metadatos
de los chunks para que `generador.py` funcione correctamente.

## Archivos requeridos

| Archivo          | Descripción                                                    |
|------------------|----------------------------------------------------------------|
| `index.faiss`    | Índice FAISS con los vectores de los documentos.               |
| `metadata.jsonl` | Metadatos de los chunks (cada línea corresponde a un vector).  |

> **Importante:** el archivo debe llamarse exactamente `index.faiss`
> (no `indice.faiss`), ya que es el nombre que referencia el script en
> `generador.py`.

## Cómo descargar los archivos

1. Abre el siguiente enlace de Google Drive:

   https://drive.google.com/drive/folders/1c3tGyRZD3_xiCGm_7IodyY2H409THRyR

2. Dentro de la carpeta, selecciona `index.faiss` y `metadata.jsonl`.

3. Haz clic derecho (o usa el menú de tres puntos) y elige **Descargar**.

4. Mueve (o guarda) ambos archivos en esta misma carpeta:

   ```
   entrega/base_vectorial/encoder_multilingual/
   ```

Al finalizar, la carpeta debe quedar así:

```
base_vectorial/encoder_multilingual/
├── index.faiss
├── metadata.jsonl
└── README.md
```
