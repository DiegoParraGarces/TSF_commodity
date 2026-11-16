# Pronóstico del precio del azúcar con NeuralProphet

Aplicación web que descarga el histórico del precio de los **futuros del azúcar n.º 11** (ticker `SB=F`) y pronostica sus próximos días con un modelo de redes neuronales para series de tiempo. Muestra el pronóstico junto con un **intervalo de incertidumbre** (percentiles 10 y 90), útil para planear compras o coberturas de una materia prima volátil.

## Qué hace

- Descarga precios de cierre diarios desde Yahoo Finance (`yfinance`).
- Permite elegir cuántos años de histórico usar (1 a 11) y cuántos días pronosticar (1 a 14).
- Entrena un modelo **NeuralProphet** con:
  - estacionalidad anual y semanal,
  - 50 puntos de cambio de tendencia,
  - componente autorregresivo con 30 rezagos y capas ocultas `[21, 21]`,
  - regresión por cuantiles para el intervalo 10 %–90 %,
  - parada temprana con 20 % de los datos como validación.
- Reporta **MAE** y **RMSE** de validación y grafica histórico, pronóstico e intervalo con Plotly.

## Cómo ejecutarlo

```bash
pip install -r requirements.txt
streamlit run app.py
```

La app abre en el navegador. El primer entrenamiento puede tardar uno o dos minutos.

**Herramientas:** Python, NeuralProphet (PyTorch), Streamlit, yfinance, pandas, Plotly.

## Próximos pasos

- Comparar contra un modelo de referencia (último valor observado o media móvil).
- Guardar el modelo entrenado para no reentrenar en cada visita.
- Desplegar la app en Streamlit Community Cloud.

## Autor

Diego Parra · [LinkedIn](https://www.linkedin.com/in/diegoparragar)
