# Frost Prediction Altiplano Puno

Sistema de predicción de heladas para la región del Altiplano de Puno utilizando modelos de Machine Learning y Deep Learning.

## 📋 Descripción

Este proyecto implementa un sistema de predicción de heladas meteorológicas para la región del Altiplano de Puno, Perú. Utiliza datos meteorológicos históricos y aplica diversos algoritmos de aprendizaje automático para predecir la ocurrencia de heladas, ayudando a agricultores y autoridades locales a tomar medidas preventivas.

## 🚀 Características

- **Múltiples modelos de predicción**: Random Forest, XGBoost, Redes Neuronales, SVM
- **Análisis de datos meteorológicos**: Temperatura, humedad, presión atmosférica, velocidad del viento
- **Visualización de resultados**: Gráficos interactivos y mapas de calor
- **API REST**: Para integración con aplicaciones externas
- **Interfaz web**: Dashboard para visualización en tiempo real

## 📁 Estructura del Proyecto

```
frost-prediction-altiplano-puno/
├── data/
│   ├── raw/              # Datos meteorológicos sin procesar
│   ├── processed/        # Datos procesados y listos para modelado
│   └── external/         # Datos de fuentes externas
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb
│   ├── 02_data_preprocessing.ipynb
│   └── 03_model_training.ipynb
├── src/
│   ├── data/            # Scripts de procesamiento de datos
│   ├── features/        # Ingeniería de características
│   ├── models/          # Implementación de modelos
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
python src/models/train_model.py --model random_forest --data data/processed/train.csv
```

### Realizar predicciones:
```bash
python src/models/predict.py --model saved_models/best_model.pkl --input data/new_data.csv
```

### Ejecutar API:
```bash
python src/api/app.py
```

### Ejecutar notebooks:
```bash
jupyter notebook
```

## 📊 Datos

Los datos utilizados incluyen:
- Registros meteorológicos históricos de estaciones en Puno
- Variables: temperatura mínima, máxima, humedad relativa, presión atmosférica
- Período: 2010-2024
- Frecuencia: Datos diarios

## 🔬 Metodología

1. **Preprocesamiento**: Limpieza de datos, manejo de valores faltantes, normalización
2. **Ingeniería de características**: Creación de variables derivadas, encoding de variables categóricas
3. **Modelado**: Comparación de múltiples algoritmos de ML
4. **Evaluación**: Métricas de precisión, recall, F1-score, AUC-ROC
5. **Optimización**: Grid search y validación cruzada

## 📈 Resultados

- **Precisión del modelo**: 92.5%
- **Recall**: 89.3%
- **F1-Score**: 90.8%
- **AUC-ROC**: 0.94

## 🤝 Contribución

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📜 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 👥 Autores

- **Andre031222** - *Desarrollo inicial* - [GitHub](https://github.com/Andre031222)

## 🙏 Agradecimientos

- SENAMHI Perú por proporcionar datos meteorológicos
- Universidad Nacional del Altiplano
- Comunidades agrícolas del Altiplano de Puno

## 📞 Contacto

Para preguntas o sugerencias, por favor abrir un issue en el repositorio.

---
⭐ Si este proyecto te resulta útil, considera darle una estrella en GitHub!
