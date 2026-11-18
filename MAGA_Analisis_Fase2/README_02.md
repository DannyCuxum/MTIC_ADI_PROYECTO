# Fase 2 · Notebook 02 — Análisis exploratorio de precios agrícolas (MAGA)

**Maestría TIC — Análisis de la Información, USAC**  
**Proyecto:** Análisis del comportamiento histórico y predicción de precios de productos agrícolas seleccionados en Guatemala.  
**Ámbito:** mercado La Terminal, enero de 1998 a julio de 2026.

## Dependencia estricta

Este notebook consume el archivo generado por `01_preparacion_datos.ipynb`:

`data/prepared/maga_precios_mensuales_la_terminal_1998_2026.csv`

También verifica, cuando está disponible, la procedencia y huella digital reportadas en `outputs/01_metadata_procedencia.json`. No modifica la información original ni el CSV preparado del Notebook 01. Se esperan 343 registros por producto (tomate de cocina, papa Loman y chile pimiento), un total de 1,029.

## Ejecución en Google Colab

1. Abrir `02_analisis_exploratorio.ipynb` desde Google Drive mediante **Abrir con → Google Colaboratory**.
2. Elegir **Entorno de ejecución → Ejecutar todas** y autorizar el montaje de Google Drive.
3. Confirmar que la carpeta del proyecto se llama `MAGA_Analisis_Fase2` y está en `Mi unidad`.
4. Verificar al final el mensaje `✓ Notebook 02 ejecutado y resultados exportados.`
5. Consultar `outputs/02_analisis_exploratorio/` para revisar las figuras PNG, tablas CSV y la síntesis Markdown/JSON.

No es necesario cargar de nuevo el ZIP mensual si el Notebook 01 ya creó el CSV preparado. Si el archivo de entrada falta, el cuaderno se detiene con una indicación explícita para ejecutar primero el Notebook 01.

## Ejecución local opcional

```bash
export MAGA_PROJECT_DIR="/ruta/a/MAGA_Analisis_Fase2"
# abrir notebook en Jupyter y ejecutar sus celdas
```

Dependencias: Python 3, pandas, NumPy, Matplotlib, scikit-learn, IPython (preinstaladas normalmente en Colab).

## Preguntas y técnicas

| Pregunta original | Evidencia |
|---|---|
| P1. Evolución histórica | Serie de precios y promedios móviles descriptivos |
| P2. Variabilidad y frecuencia | Cambios porcentuales, medidas de dispersión, meses con cambio ≥20% |
| P3. Patrones temporales | Variaciones medianas por mes y comparación de subperíodos |
| P4. Fluctuaciones relevantes | Mayores movimientos mensuales y marcas robustas MAD |
| Relaciones y grupos | Spearman sobre cambios mensuales, K-means sobre 81 producto–años completos |

Las gráficas y estadísticas se generan a partir del CSV original preparado, no a partir de cifras transcritas manualmente. Las comparaciones entre productos utilizan cambios relativos por la diferencia en unidades comerciales.

## Advertencias metodológicas

- Los precios nominales no se han ajustado por inflación.
- Los grupos exploratorios no son pronósticos ni demuestran causalidad.
- Los cambios mensuales extremos se conservan; no se eliminan como errores por su magnitud.
- El Notebook 02 no realiza entrenamiento predictivo ni resuelve la quinta pregunta de investigación. El pronóstico del precio del mes siguiente mediante Regresión Lineal Múltiple corresponde al Notebook 03.
- En el informe de la Fase 2 conviene seleccionar **solo las visualizaciones de mayor valor**, no incorporar todas las gráficas del notebook.

**Fuente de datos:** [MAGA – SIM, Datos abiertos](https://precios.maga.gob.gt/otros/datos-abiertos/).  
**Referencia metodológica:** Myatt y Johnson (2014), *Making Sense of Data I*, 2.ª edición.
