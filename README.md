# Frost Prediction Altiplano Puno

Sistema de predicción de heladas para la región del Altiplano de Puno utilizando modelos de Machine Learning y Deep Learning.

## 📋 Descripción

Este proyecto implementa un sistema de predicción de heladas meteorológicas para la región del Altiplano de Puno, Perú. Utiliza datos meteorológicos históricos y aplica diversos algoritmos de aprendizaje automático para predecir la ocurrencia de heladas, ayudando a agricultores y autoridades locales a tomar medidas preventivas.

## 👥 Autores

- **Richar Andre Vilca Solorzano** - *Desarrollo principal*
  - Universidad Nacional del Altiplano, Puno
  - Email: andrevilcasolorzano@gmail.com
  - ORCID: 0009-0003-2385-5263
  - [GitHub](https://github.com/Andre031222)

- **Dina Maribel Yana Yucra** - *Co-autora*
  - Universidad Nacional del Altiplano, Puno
  - Email: maribelbel201314@gmail.com
  - ORCID: 0009-0003-6218-2735

- **Fred Torres Cruz** - *Supervisor*
  - Universidad Nacional del Altiplano, Puno
  - Email: ftorres@unap.edu.pe
  - ORCID: 0000-0003-0834-6834

## 🚀 Características

- **Múltiples modelos de predicción**: 12 modelos comparados incluyendo Random Forest, XGBoost, LSTM, CNN-1D, y un modelo Ensemble
- **Análisis de datos meteorológicos**: Temperatura, humedad, presión atmosférica, velocidad del viento
- **Visualización de resultados**: Gráficos interactivos y mapas de calor
- **API REST**: Para integración con aplicaciones externas
- **Interfaz web**: Dashboard para visualización en tiempo real
- **Datos satelitales**: Utiliza NASA POWER con 121,056 observaciones (2000-2025)

## 📊 Resultados del Estudio

### Rendimiento de los Modelos (Test Set 2024-2025)

| Modelo | RMSE (°C) | MAE (°C) | R² | TSS | AUC |
|--------|-----------|----------|-----|-----|-----|
| **Ensemble** | **1.65** | **1.12** | **0.931** | **0.87** | **0.96** |
| XGBoost | 1.78 | 1.19 | 0.918 | 0.81 | 0.95 |
| Random Forest | 1.83 | 1.24 | 0.912 | 0.79 | 0.94 |
| LSTM | 1.89 | 1.31 | 0.905 | 0.80 | 0.94 |
| CNN-1D | 1.96 | 1.38 | 0.897 | 0.77 | 0.93 |
| SVM | 2.15 | 1.58 | 0.871 | 0.71 | 0.90 |
| SARIMA+ANN | 2.21 | 1.65 | 0.862 | 0.73 | 0.91 |
| MLP | 2.28 | 1.71 | 0.848 | 0.70 | 0.89 |
| Prophet | 2.31 | 1.76 | 0.842 | 0.69 | 0.89 |
| STL+ARIMA | 2.38 | 1.82 | 0.836 | 0.67 | 0.88 |
| SARIMAX | 2.52 | 1.89 | 0.821 | 0.65 | 0.88 |
| Holt-Winters | 3.14 | 2.41 | 0.758 | 0.58 | 0.82 |

### Hallazgos Clave

- ✅ El modelo **Ensemble** logró una mejora del **35%** sobre los métodos estadísticos tradicionales
- ✅ **LSTM** demostró la mejor capacidad para detectar eventos extremos de helada (Recall=0.88)
- ✅ Las predicciones mantienen utilidad hasta **3 días** de anticipación
- ✅ Variables más importantes: Temperatura mínima del día anterior (32%), indicadores estacionales (18%)

## 📁 Estructura del Proyecto

```
frost-prediction-altiplano-puno/
├── data/
│   ├── raw/              # Datos meteorológicos sin procesar
│   ├── processed/        # Datos procesados y listos para modelado
│   └── external/         # Datos de fuentes externas (NASA POWER)
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb
│   ├── 02_data_preprocessing.ipynb
│   ├── 03_model_training.ipynb
│   └── 04_model_evaluation.ipynb
├── src/
│   ├── data/            # Scripts de procesamiento de datos
│   ├── features/        # Ingeniería de características
│   ├── models/          # Implementación de modelos
│   │   ├── statistical/ # ARIMA, Prophet, etc.
│   │   ├── ml/         # Random Forest, XGBoost, SVM
│   │   ├── deep/       # LSTM, CNN-1D, MLP
│   │   └── ensemble/   # Modelo ensemble
│   ├── visualization/   # Scripts de visualización
│   └── api/            # API REST
├── tests/              # Pruebas unitarias
├── docs/               # Documentación
├── requirements.txt    # Dependencias del proyecto
└── README.md
```

## 🛠️ Instalación

1. Clonar el repositorio:
```bash
git clone https://github.com/Andre031222/frost-prediction-altiplano-puno.git
cd frost-prediction-altiplano-puno
```

2. Crear entorno virtual:
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

3. Instalar dependencias:
```bash
pip install -r requirements.txt
```

## 💻 Uso

### Entrenamiento de modelos:
```bash
# Entrenar modelo individual
python src/models/train_model.py --model xgboost --data data/processed/train.csv

# Entrenar todos los modelos
python src/models/train_all_models.py
```

### Realizar predicciones:
```bash
# Predicción con modelo ensemble
python src/models/predict.py --model ensemble --input data/new_data.csv

# Predicción para una fecha específica
python src/models/predict.py --date 2025-07-15 --station Mazocruz
```

### Ejecutar API:
```bash
python src/api/app.py
# API disponible en http://localhost:8000
```

### Ejecutar notebooks:
```bash
jupyter notebook
```

## 📊 Datos

**Fuente**: NASA POWER (Prediction Of Worldwide Energy Resources)

**Características del dataset**:
- **Período**: Enero 2000 - Febrero 2025
- **Observaciones**: 121,056 registros
- **Estaciones**: 13 ubicaciones en el Altiplano de Puno
- **Variables**: 
  - Temperatura mínima y máxima (T2M_MIN, T2M_MAX)
  - Humedad relativa (RH2M)
  - Presión atmosférica (PS)
  - Velocidad del viento (WS2M)
  - Precipitación (PRECTOTCORR)
  - Rango de temperatura diario (T2M_RANGE)

## 🔬 Metodología

1. **Preprocesamiento**: 
   - Limpieza de datos y manejo de valores faltantes
   - Normalización y estandarización
   - Creación de variables temporales y estacionales

2. **Modelos implementados**:
   - **Estadísticos**: SARIMAX, Holt-Winters, Prophet, STL+ARIMA
   - **Machine Learning**: Random Forest, SVM, XGBoost
   - **Deep Learning**: MLP, LSTM, CNN-1D
   - **Híbridos**: SARIMA+ANN
   - **Ensemble**: Combinación ponderada de XGBoost, LSTM y Random Forest

3. **Evaluación**: 
   - División temporal: 2000-2023 (entrenamiento), 2024-2025 (prueba)
   - Métricas: RMSE, MAE, R², Precisión, Recall, F1-Score, TSS, AUC-ROC
   - Validación cruzada con 5 bloques temporales

## 📈 Visualizaciones

El proyecto incluye visualizaciones interactivas de:
- Evolución temporal de temperaturas
- Mapas de distribución espacial de heladas
- Comparación de predicciones vs observaciones
- Análisis de errores por estación y período
- Importancia de variables predictoras

## 🤝 Contribución

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/NuevaCaracteristica`)
3. Commit tus cambios (`git commit -m 'Agregar nueva característica'`)
4. Push a la rama (`git push origin feature/NuevaCaracteristica`)
5. Abre un Pull Request

## 📜 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 🙏 Agradecimientos

- **SENAMHI Perú** por proporcionar datos meteorológicos de validación
- **NASA** por el acceso abierto a datos POWER
- **Universidad Nacional del Altiplano** por el apoyo institucional
- **Comunidades agrícolas del Altiplano de Puno** por su colaboración

## 📞 Contacto

Para preguntas, sugerencias o colaboraciones:
- Abrir un issue en el repositorio
- Email: andrevilcasolorzano@gmail.com

## 📚 Publicación

Este trabajo fue publicado en:

**International Journal of Advanced Computer Science and Applications (IJACSA)**  
Vol. 1, No. 1, 2025  
DOI: [Por asignar]

---
⭐ Si este proyecto te resulta útil, considera darle una estrella en GitHub!
