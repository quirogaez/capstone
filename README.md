<!-- Badges -->
[![Build Status](https://img.shields.io/github/actions/workflow/status/quirogaez/capstone/ci.yml?branch=main)](https://github.com/quirogaez/capstone/actions)
[![DVC Status](https://img.shields.io/badge/DVC-enabled-brightgreen)](https://dvc.org)
[![Python Version](https://img.shields.io/badge/python-3.9%2B-blue)]()

# 🧠 Capstone Project – Detección Inteligente de Neumonía en Radiografías de Tórax

> **Propuesta SIC 2024**  
> *“Aplicando CNNs preentrenadas y generación adversarial para asistir el diagnóstico médico”*

---

## 🩺 Descripción general

Este proyecto presenta el diseño e implementación de un sistema de inteligencia artificial para detectar **automáticamente la neumonía** en imágenes de rayos X pediátricos.  

El sistema emplea **redes neuronales convolucionales (CNN)** con aprendizaje por transferencia, procesamiento avanzado de imágenes y técnicas como **DCGANs** para abordar el desbalance de clases. También se exploran métodos inspirados en [este artículo de ArXiv (2024)](https://arxiv.org/html/2410.15437v1) para mejorar la clasificación multicategoría.

🔍 **Objetivo general**: Construir un modelo de inteligencia artificial mediante una red neuronal convolucional (CNN) pre entrenada para detectar y localizar las zonas afectadas por la presencia de neumonía a partir de radiografías de tórax.

---

## ⚙️ Características Clave del Modelo

- ✅ Clasificación multiclase: Neumonía bacteriana, neumonía viral y casos normales.
- 🧠 Arquitectura final: **VGG16** con pesos preentrenados y cabeza personalizada.
- 🔄 Balanceo de clases con **GANs**, logrando uniformidad de clases y mejor generalización.
- 🔍 **Grad-CAM** como herramienta de interpretabilidad visual, aplicada a predicciones clínicas.
- 📊 Resultados sólidos: Accuracy del 87.18% y F1-scores > 80% en todas las clases.

---

## 🗂️ Estructura del repositorio

| Ruta                        | Descripción                                                                                   |
|----------------------------|-----------------------------------------------------------------------------------------------|
| `notebooks/`               | Notebooks principales (EDA, entrenamiento, evaluación, GANs)                                 |
| `data/raw/`                | Radiografías originales del dataset de Kaggle                                                 |
| `data/processed/`          | Imágenes segmentadas, normalizadas y aumentadas                                              |
| `src/data/`                | Scripts de carga, segmentación y transformación                                               |
| `src/models/`              | Definición de modelos CNN, fine-tuning                                                        |
| `src/evaluation/`          | Funciones de métricas, gráficos y análisis                                                    |
| `experiments/`             | Configs de entrenamiento (YAML) y logs                                                        |
| `models/`                  | Pesos y artefactos generados por los modelos entrenados                                       |
| `logs/`                    | Logs generados por DVC y ejecución del pipeline                                               |
| `reports/`                 | Informes y presentaciones técnicas                                                            |
| `tests/`                   | Pruebas unitarias de componentes                                                              |
| `.github/workflows/`       | Pipeline de CI con validación automática                                                      |
| `dvc.yaml` / `.dvc/`       | Pipeline de datos y modelos con [DVC](https://dvc.org)                                         |
| `requirements.txt`         | Dependencias del entorno                                                                      |
| `README.md`                | Este archivo                                                                                  |

---

## 🔁 Flujo de Trabajo del Proyecto

1. **Carga y exploración de datos**: Se importan imágenes del dataset Chest X-ray (Pneumonia) y se realiza inspección visual, verificación de integridad y preprocesamiento.
2. **Preprocesamiento**: Redimensionamiento a 224x224, normalización, y estructuración del conjunto en carpetas `train/`, `val/`, y `test/`.
3. **Balanceo de clases**:
   - Se implementaron técnicas de **undersampling** y **data augmentation** inicialmente.
   - En el enfoque final, se entrenó un modelo **DCGAN** para generar imágenes sintéticas de clases minoritarias y lograr equilibrio (2530 imágenes por clase).
4. **Entrenamiento del modelo**:
   - Se utilizó **VGG16 preentrenado** sobre ImageNet.
   - Entrenamiento en dos fases: congelamiento de capas base + fine-tuning.
5. **Evaluación**:
   - Se utilizó accuracy, precision, recall y F1-score, tanto global como por clase.
   - Se generó una matriz de confusión para analizar errores.
6. **Interpretabilidad con Grad-CAM**:
   - Se aplicó Grad-CAM para resaltar regiones pulmonares relevantes.
   - Las visualizaciones se superpusieron sobre la imagen original para facilitar su interpretación clínica. 

---

## 📊 Resultados Finales

| Clase               | Precision | Recall | F1-Score |
|--------------------|-----------|--------|----------|
| Normal             | 94.90%    | 79.49% | 86.51%   |
| Neumonía Bacteriana| 87.31%    | 96.69% | 91.76%   |
| Neumonía Viral     | 77.50%    | 83.78% | 80.52%   |
| **Promedio Macro** | 86.57%    | 86.66% | 82.27%   |
| **Accuracy total** |           |        | **87.18%** |

---

## 🖼️ Visualizaciones con Grad-CAM

| Clase               | Imagen |
|--------------------|--------|
| Neumonía Bacteriana| ![](gradcam/gradcam_bacterial.jpg) |
| Neumonía Viral     | ![](gradcam/gradcam_viral.jpg) |
| Normal             | ![](gradcam/gradcam.png) |

---

## 📌 Dataset

- Fuente: [Chest X-ray Pneumonia Dataset – Kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia/data)  
- Tipo: Radiografías pediátricas clasificadas en **Normal**, **Neumonía Viral**, **Neumonía Bacteriana**

---

## 📦 Instalación

```bash
git clone https://github.com/quirogaez/capstone.git
cd capstone
pip install -r requirements.txt


