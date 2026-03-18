# Brecha-Digital

Modelo que identifica zonas geográficas con riesgo de exclusión digital para optimizar la entrega de ayudas gubernamentales. Idea central: **«Distrito → se predice el nivel de pobreza digital → se asigna prioridad de ayuda»**.

## Stack tecnológico

| Parte | Tecnologías |
|-------|-------------|
| **ML (Colab)** | Python 3, pandas, NumPy, scikit-learn (LinearRegression, DecisionTreeClassifier, train_test_split), TensorFlow/Keras (Sequential, Dense), matplotlib |
| **Simulador web** | React 18, Vite 5, CSS (sin framework UI); alternativa: un solo HTML + CSS + JS vanilla |
| **API** | Node.js, Express 4, CORS; lógica de predicción en JS (misma fórmula que el notebook) |

El front no depende del backend: la predicción se hace en el navegador con la fórmula de la regresión (coeficientes exportados desde el notebook).

## Contenido del proyecto

- **colab_digital_poverty.ipynb** — Notebook ML (Colab): datos sintéticos, regresión lineal, árbol de decisión (prioridad), red neuronal simple y visualización. Incluye coeficientes para el simulador web.
- **simulator/** — Aplicación React (Vite) «Digital Poverty Simulator»: sliders (ingreso, educación, desempleo), nivel de internet, riesgo y prioridad de ayuda; sección «Mejora el distrito».
- **simulator.html** — Simulador en un solo archivo (sin npm): **mapa de España por comunidades autónomas** (Leaflet + GeoJSON), diseño lúdico, regiones con colores distintos y nombres visibles; layout con mapa a la izquierda y controles (sliders, cartas, progreso) a la derecha. El usuario elige una región en el mapa y ajusta ingreso, educación y desempleo; el progreso global («X de 19 regiones con riesgo bajo») se actualiza al instante.
- **api/** — API opcional (Express): `POST /predict` con `{ income, unemployment, education }` devuelve `{ internet_access, priority }`.
- **mapa_brecha_digital.html** / **copy_of_proyecto_brecha_digital_maps_real.py** — Mapa y modelo con datos INE existentes.

## Cómo ejecutar

- **Simulador React:** `cd simulator && npm install && npm run dev`
- **Simulador HTML:** abrir `simulator.html` en el navegador.
- **API:** `cd api && npm install && npm start` (puerto 3001 por defecto).
