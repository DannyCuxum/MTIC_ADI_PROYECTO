### Respuesta a la pregunta de investigación 5

Se aplicó **Regresión Lineal Múltiple**, con la misma configuración **D · Medio plazo** y un modelo entrenado por producto. La selección se sustentó en validación progresiva 2022–2023; la evaluación retrospectiva se realizó para enero de 2024–julio de 2026 (**31 meses por producto**).

- **Tomate:** MAE de **Q32.59** por caja (45 - 50 lb), RMSE de **Q54.20** y MAPE de **18.9%**; mejora **30.0%** frente a repetir el precio anterior.
- **Papa Loman:** MAE de **Q43.55** por quintal, RMSE de **Q64.58** y MAPE de **11.5%**; mejora **9.0%** frente a repetir el precio anterior.
- **Chile pimiento:** MAE de **Q31.58** por caja (90 -100 unidades), RMSE de **Q43.75** y MAPE de **27.2%**; mejora **7.4%** frente a repetir el precio anterior.

**Control de consistencia:** en los seis casos de validación 2022–2023 (tres productos por dos años), la configuración elegida superó la referencia en **0 de 6**; su razón media MAE(modelo)/MAE(referencia) fue **1.112**. Esto advierte que el comportamiento predictivo depende del período y que no es correcto seleccionar el modelo únicamente por los buenos resultados posteriores.

**Balance de evaluación:** la regresión redujo el error de referencia en **3 de 3** productos durante 2024–julio de 2026. El resultado responde **con qué magnitud de error** se pueden estimar precios un mes adelante, pero no constituye garantía de exactitud en meses futuros.

**Limitaciones:** precios nominales; unidades comerciales diferentes; rezagos correlacionados; ausencia de variables explicativas externas; posible inestabilidad ante cambios bruscos; modelo entrenado hasta 2023 para la evaluación y precios reales anteriores conocidos en cada estimación. Las pruebas preliminares anteriores a este notebook ya habían observado parte de 2024–2026, por lo que no se trata de una evaluación históricamente desconocida en todas las etapas del proyecto.

**Continuidad:** los resultados del Notebook 03 complementan las preguntas 1–4 resueltas en el Notebook 02; las figuras, métricas, predicciones y limitaciones sirven de insumo para el informe de Fase 2 y la comunicación de Fase 3. La estimación de agosto de 2026 no se usa para calcular errores.