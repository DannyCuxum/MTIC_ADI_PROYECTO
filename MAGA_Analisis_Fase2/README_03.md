# MAGA · Análisis de la Información · Fase 2
## Notebook 03 — Modelado predictivo

**Proyecto de la Maestría en Tecnologías de Información y Comunicaciones (USAC).**

### Propósito
Responder la quinta pregunta de investigación de la Fase 1: determinar el error de pronosticar a un mes los precios de tomate de cocina, papa Loman y chile pimiento del mercado La Terminal (MAGA). La preparación proviene del Notebook 01 y los hallazgos descriptivos del Notebook 02.

### Método
- Modelo único como **familia metodológica**: Regresión Lineal Múltiple (`LinearRegression`, mínimos cuadrados ordinarios); un ajuste independiente por producto, variables comunes.
- Datos: 1,029 registros originales preparados (343 por producto, enero 1998–julio 2026). Construcción de rezagos 1, 2, 3, 6, 12 y mes conocido; 993 filas modelables (331 por producto).
- Selección de la configuración común de variables mediante **dos folds cronológicos** (2022 y 2023), comparando MAE relativo a repetir el último precio.
- Evaluación: coeficientes entrenados hasta diciembre de 2023, evaluados en 31 meses de enero 2024 a julio 2026, como pronósticos sucesivos **a un mes**, con precios del mes anterior efectivamente observados en cada momento.
- Métricas: MAE (principal), RMSE, MAPE, sesgo y reducción del MAE frente a referencia.
- Proyección adicional: agosto 2026, fecha siguiente a la última registrada en el archivo. No es un pronóstico vigente de noviembre ni puede calificarse por acierto sin dato observado.

### Resultados principales (evaluación retrospectiva)

| Producto | MAE regresión | MAE último precio | Reducción de MAE | MAPE regresión |
|---|---:|---:|---:|---:|
| Tomate | Q32.59 | Q46.58 | 30.0 % | 18.85 % |
| Papa Loman | Q43.55 | Q47.87 | 9.0 % | 11.51 % |
| Chile pimiento | Q31.58 | Q34.12 | 7.4 % | 27.23 % |

**Limitación sustantiva:** en los seis pares producto-año de la validación 2022–2023, la regresión no superó la referencia en ninguno; la razón MAE promedio fue 1.112. Que el período de evaluación posterior sí registre mejoría no garantiza estabilidad predictiva. Los datos 2024–2026 fueron conocidos parcialmente por el equipo durante exploraciones previas; no se afirma desconocimiento histórico total de ese tramo.

### Abrir en Google Colab
1. Abrir `notebooks/03_modelado_predictivo.ipynb` en Google Drive.
2. Usar **Abrir con → Google Colaboratory** (no Google Docs ni Sheets).
3. Ejecutar **Entorno de ejecución → Ejecutar todas** y autorizar acceso a Google Drive si Colab lo solicita.
4. El notebook busca automáticamente `MyDrive/MAGA_Analisis_Fase2/data/prepared/maga_precios_mensuales_la_terminal_1998_2026.csv`, producido en Notebook 01.
5. Se comprueban huellas SHA-256 con `outputs/01_metadata_procedencia.json` y `outputs/02_analisis_exploratorio/02_manifiesto_resultados.json`, si están disponibles.

### Estructura de salidas
- `outputs/03_modelado_predictivo/`: auditoría, matriz de predictores, validación y selección, predicciones por mes, métricas, coeficientes, análisis anual, gráficas, síntesis y manifiesto reproducible.
- `models/`: tres modelos `joblib` entrenados hasta julio 2026. **Cargar solo archivos provenientes de fuentes confiables.**
- En el paquete descargable se incluye una copia del `.ipynb` sin ejecutar, otra con resultados de las pruebas, el CSV preparado y las evidencias.

### Alcance y coherencia entre notebooks
Notebook 01: auditoría, selección y estandarización del archivo MAGA.
Notebook 02: preguntas de investigación 1–4, tendencias, volatilidad, estacionalidad, atípicos, relaciones y agrupaciones.
Notebook 03: pregunta 5, Regresión Lineal Múltiple, pronósticos y discusión de los errores.

**Referencia oficial:** https://precios.maga.gob.gt/otros/datos-abiertos/
**Documentación algoritmo:** https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html
