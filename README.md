# 📊 S&P 500 ESG Risk Analysis

**Análisis exploratorio de riesgo ESG (Environmental, Social, Governance)** en las 503 empresas del índice S&P 500, identificando patrones sectoriales de riesgo, empresas outlier y la composición del riesgo ESG total.

---

## 📋 Contexto y objetivo

Simulación de un encargo real para un equipo de inversión sostenible que necesita responder:

1. ¿Qué sectores del S&P 500 presentan mayor riesgo ESG en promedio?
2. ¿Existen empresas "outlier" con riesgo desproporcionado frente a su propio sector?
3. ¿Qué dimensión del ESG (Ambiental, Social o Gobernanza) pesa más en el riesgo total?
4. ¿Qué empresas serían candidatas a revisión prioritaria para un fondo de inversión responsable?

---

## 📁 Estructura del proyecto

```
esg-sp500-risk-analysis/
│
├── data/
│   └── sp500_esg_risk_ratings.csv      # Dataset original (503 empresas)
│
├── notebooks/
│   └── esg_sp500_analysis.ipynb         # Análisis completo paso a paso
│
├── visuals/
│   ├── riesgo_esg_por_sector.png
│   ├── componentes_esg_promedio.png
│   └── correlacion_componentes_esg.png
│
└── README.md
```

---

## 🗃️ Fuente de datos

**S&P 500 ESG Risk Ratings** — [Kaggle](https://www.kaggle.com/datasets/pritish509/s-and-p-500-esg-risk-ratings)

- 503 empresas del índice S&P 500
- Scores de riesgo Ambiental, Social y de Gobernanza por separado, más score total
- Nivel de controversia y percentil de riesgo ESG

---

## 🔧 Metodología

### 1. Limpieza de datos
- Eliminación de 73 empresas sin score ESG calculado (14.5% del dataset) — decisión justificada por tratarse de evaluaciones cualitativas no imputables de forma confiable
- Eliminación de 1 registro sin sector asignado

### 2. Análisis exploratorio (EDA)
- Riesgo ESG promedio, mediana y desviación estándar por sector
- Comparación de los tres componentes del riesgo: Ambiental, Social, Gobernanza
- Matriz de correlación entre componentes

### 3. Detección de outliers
- Cálculo de z-score del riesgo ESG **dentro de cada sector** (no en términos absolutos)
- Empresas con desviación superior a 1.5 desviaciones estándar respecto a su sector

---

## 📊 Principales hallazgos

### Riesgo por sector
**Energy** (32.3 promedio), **Basic Materials** (26.7) y **Utilities** (26.7) lideran el riesgo ESG, consistente con la intensidad de emisiones de su actividad. **Real Estate** (13.1) y **Technology** (16.9) presentan el menor riesgo promedio.

### El componente que más pesa no es el esperado
> 💡 **Hallazgo clave:** el riesgo **Social** (9.07 promedio) supera al riesgo de **Gobernanza** (6.73) y **Ambiental** (5.74). La narrativa pública sobre ESG suele centrarse en lo ambiental, pero los datos muestran que el componente social es el de mayor peso relativo en el riesgo total.

### Empresas outlier
Se identificaron **30 empresas** (de 430 con score válido) con riesgo significativamente superior al promedio de su propio sector. Casos destacados: **Wells Fargo & Co.** y **Fortive Corporation**, con desviaciones superiores a 3 desviaciones estándar frente a sus respectivos sectores — señal de riesgo idiosincrático, no sectorial.

### Mayor y menor riesgo absoluto
| Mayor riesgo ESG | Sector | Score |
|---|---|---|
| Occidental Petroleum | Energy | 41.7 |
| Exxon Mobil | Energy | 41.6 |
| General Electric | Industrials | 40.5 |

| Menor riesgo ESG | Sector | Score |
|---|---|---|
| Hasbro, Inc. | Consumer Cyclical | 7.1 |
| Keysight Technologies | Technology | 7.6 |
| CBRE Group | Real Estate | 8.0 |

---

## 🎯 Conclusión ejecutiva

Cualquier estrategia de screening ESG debe **normalizar por sector** antes de comparar empresas: el riesgo "alto" o "bajo" depende fuertemente de la industria de referencia. Una petrolera con riesgo 30 puede estar dentro de lo esperado para su sector, mientras que un banco con el mismo score sería una señal de alerta grave.

---

## 🛠️ Stack técnico

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-green)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12-teal)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-orange)

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## ▶️ Cómo reproducir el análisis

```bash
git clone https://github.com/tu-usuario/esg-sp500-risk-analysis.git
cd esg-sp500-risk-analysis
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook notebooks/esg_sp500_analysis.ipynb
```

---

## 👩‍💻 Autora

**Naiara Altuna Renedo**  
Data Analyst · Medio Ambiente & Sostenibilidad  
📍 Playa del Carmen, México · Disponible para trabajo remoto  
🔗 [LinkedIn](https://linkedin.com/in/naiara-altuna) · 📧 naiaraaltuna@gmail.com

---

*Dataset: S&P 500 ESG Risk Ratings (Kaggle) · Análisis elaborado en Python (pandas, matplotlib, seaborn)*
