<!-- badges -->
[![Build Status](https://img.shields.io/github/actions/workflow/status/quirogaez/capstone/ci.yml?branch=main)](https://github.com/quirogaez/capstone/actions)
[![DVC Status](https://img.shields.io/badge/DVC-enabled-brightgreen)](https://dvc.org)
[![Python Version](https://img.shields.io/badge/python-3.9%2B-blue)]()

# 🩺 Detección y Clasificación Inteligente de Neumonía por Radiografía

> **Capstone Project** – Propuesta SIC 2024  
> *“Aplicando CNNs -- - para transformar el diagnóstico de neumonía”*

---

## 📖 Descripción

En este Capstone abordamos un desafío de salud pública: **detectar y clasificar neumonía** en radiografías de tórax usando Redes Neuronales Convolucionales (ESPECIFICAR). Partiendo del dataset real de Kaggle <https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia/data>, implementamos desde un modelo **baseline** hasta arquitecturas avanzadas (ResNet, DenseNet, --).

---

## 🚀 Características principales

- **Experimentación guiada** en Colab  
- **Modelos**:
- **Manejo de clases desbalanceadas**: class‐weighting, data augmentation  
- **Evaluación rigurosa**: precisión, recall, F1, AUC‐ROC, matriz de confusión  
- **Análisis de falsos positivos/negativos** 

---

## 📂 Estructura del repositorio

| Carpeta / Archivo          | Descripción                                                                                     |
|----------------------------|-------------------------------------------------------------------------------------------------|
| `data/raw/`                | Radiografías originales (train/ val/ test)                                                      |
| `data/processed/`          | Imágenes preprocesadas y aumentadas                                                             |
| `notebooks/`               | • `01_EDA.ipynb`   – Análisis exploratorio<br>• |
| `src/`                     | Código modular:<br>• `data/` (descarga, preprocessing)<br>• `models/` (definición, fine‐tune)<br>• `evaluation/` (métricas, visualización)<br>• `utils/` (helpers) |
| `experiments/`             | Configuraciones y logs de cada experimento (YAML)                                               |
| `models/`                  | Pesos y artefactos entrenados ( SavedModel)                                    |
| `logs/`                    | Registros                                                                        |
| `reports/`                 | • ` s` – Informe completo<br>• `slides/` – Presentación                                         |
| `configs/`                 | Parámetros globales y específicos de ambiente                                                    |
| `tests/`                   | Pruebas unitarias para scripts y modelos                                                        |
| `.github/workflows/ci.yml` | CI: lint, tests, validación de notebooks                                                        |
| `dvc.yaml`, `.dvc/`        | Pipeline DVC para datos y modelos                                                                |
| `README.md`                | Este archivo                                                                                   |
| `requirements.txt`         | Dependencias Python                                                                             |

---

## ⚙️ Instalación

1. **Clona el repositorio**  
   ```bash
   git clone https://github.com/quirogaez/capstone.git
   cd capstone
