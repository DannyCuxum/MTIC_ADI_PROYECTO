# MAGA · Proyecto de Análisis de Información · Fase 2
## Notebook 01 — Preparación y validación de datos

**Curso:** Análisis de la Información, Maestría TIC (USAC)

Este cuaderno documenta la adquisición, inspección, diagnóstico de calidad, selección, validación temporal y exportación de los registros mensuales del Sistema de Información de Mercados del MAGA. Se desarrolló como parte de la **Fase 2** del proyecto, para producir los datos preparados que utilizarán los notebooks 02 y 03.

### Ejecutarlo en Google Colab

1. En Google Drive, abrir la carpeta `MAGA_Analisis_Fase2/notebooks` y seleccionar `01_preparacion_datos.ipynb` → **Abrir con → Google Colaboratory**.
2. En Colab, seleccionar **Entorno de ejecución → Ejecutar todas**.
3. Autorizar el acceso a Google Drive cuando Colab lo solicite. El notebook encuentra el ZIP en `MAGA_Analisis_Fase2/data/original/` y guarda automáticamente los resultados.
4. Comprobar que aparezca `✓ Todas las series cumplen...` y `✓ Preparación y exportación verificadas.`

No es necesario instalar Python ni descargar manualmente archivos: el ZIP original está en la carpeta `data/original/` de este proyecto. En caso de copiar el notebook a otra cuenta, se puede cargar ese archivo cuando lo solicite.

### Datos de entrada y alcance

- **Fuente:** MAGA, sección Datos Abiertos, conjunto mensual CSV publicado como «a octubre de 2026».
- **Período real:** enero de 1998 a julio de 2026.
- **Mercado y actor:** La Terminal, mayorista.
- **Productos:** tomate de cocina (caja 45–50 lb), papa Loman (quintal), chile pimiento (caja 90–100 unidades).
- **Cobertura:** 343 observaciones mensuales por producto, 1,029 registros preparados en total.

### Archivos que produce el notebook

- `data/prepared/maga_precios_mensuales_la_terminal_1998_2026.csv`: conjunto preparado, sin modificación del precio registrado.
- `outputs/01_auditoria_validacion.csv`: verificación por producto de continuidad mensual, duplicados y valores faltantes.
- `outputs/01_diccionario_datos.csv`: variables originales y auxiliares.
- `outputs/01_metadata_procedencia.json`: hash SHA-256 de los archivos e información de trazabilidad.
- `outputs/01_calidad_completitud.png`: visualización de disponibilidad de precios en la fuente completa y en las series seleccionadas.

### Política de calidad

Se conservan los valores originales del campo Precio, se valida que las unidades de medida sean las establecidas y se comprueba que cada mes tenga exactamente un registro con precio válido para cada serie. No se imputan datos y no se eliminan precios extremos. Un fallo de las validaciones detendrá el proceso con un mensaje explícito.

### Reproducción fuera de Colab

El notebook también admite `MAGA_PROJECT_DIR` para la carpeta de salida y `MAGA_INPUT_ZIP` para identificar la ruta del ZIP. Se probó con Python 3.13, pandas 2.2 y NumPy 2.3. No requiere paquetes especializados adicionales en Colab.

### Alcance académico

Este es únicamente el **Notebook 01**. Las respuestas a las preguntas de evolución, variación, estacionalidad y fluctuaciones de precios corresponden al **Notebook 02**, mientras que la Regresión Lineal Múltiple y su evaluación temporal corresponden al **Notebook 03**.

**Fuentes:** https://precios.maga.gob.gt/otros/datos-abiertos/ y Myatt & Johnson (2014), *Making Sense of Data I*.
