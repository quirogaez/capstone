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

## ⚙️ Características clave

- 📁 Preprocesamiento avanzado: CLAHE, normalización, segmentación pulmonar
- 🧬 Modelado con transferencia de aprendizaje: **ResNet50** ...
- 🔄 Generación de datos con **DCGAN** para clases minoritarias
- 📊 Evaluación completa: métricas, matriz de confusión, ...
- 📚 Estructura modular para entrenamiento, evaluación y experimentación reproducible

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

## 🔬 Flujo de trabajo

1. **EDA & Preprocesamiento**  
   Exploración de imágenes, análisis de clase y aplicación de CLAHE, segmentación por Sobel y resize a 224×224.

2. **Generación de datos sintéticos (DCGAN)**  
   Entrenamiento de un generador para sintetizar imágenes de clases subrepresentadas (especialmente clase "Normal").

3. **Entrenamiento del modelo**  
   Fine-tuning de **ResNet50**, usando `class_weights` y datos balanceados con GAN. Evaluación con validación cruzada.

4. **Evaluación**  
   - Métricas por clase: Precision, Recall, F1  
   - Matriz de confusión  

---

## 📊 Resultados preliminares

| Clase         | Precision | Recall | F1-score |
|---------------|-----------|--------|----------|
| Neumonía Viral     | ...      | ...   | ...     |
| Neumonía Bacteriana| ...      | ...   | ...     |
| Normal        | ...      | ...   | ...    |

> 🔍 Mejor desempeño se obtuvo con imágenes aumentadas + DCGAN + transferencia de ResNet...

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


