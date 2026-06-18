# Optimización de Telemarketing Bancario mediante Machine Learning

Este proyecto aborda un problema de negocio desde una perspectiva analítica y financiera: cómo maximizar la conversión de depósitos a plazo fijo minimizando los costes operativos de un Call Center.

A través de la experimentación con distintos algoritmos de clasificación, se ha construido un modelo capaz de identificar al 5% de los clientes con mayor propensión de compra, permitiendo aumentar las ventas manteniendo el volumen de contactos controlado.

## Impacto de Negocio y Rentabilidad (ROI)
El análisis no se limita a estudiar las métricas tradicionales ya que incorpora un simulador financiero que emplea variables reales de mercado (costes de operadora por minuto y márgenes bancarios). 

Para garantizar el rigor técnico del proyecto, los resultados de negocio se dividen en dos fases:

**1. Selección y Eficiencia (Evaluado en Validación):**
* Aumento de ventas: frente al modelo estadístico base (Regresión Logística), el modelo XGBoost optimizado logró saltar de 133 a 142 depósitos captados manteniendo el mismo esfuerzo (226 llamadas).
* Eficiencia operativa: estas 9 ventas adicionales no generaron costes adicionales para la campaña.
* Control de riesgo: se seleccionó un modelo conservador para minimizar el riesgo de sobreajuste (apenas un 0.28%).

**2. Simulador Financiero (Evaluado en Test):**
* Rentabilidad Demostrada: al simular el modelo sobre un conjunto de datos nunca antes visto por el algoritmo, la campaña dirigida al top 5% generó un **beneficio neto estimado de +1399.22 €**.
* Retorno de Inversión: la alta precisión en la selección de clientes se traduce en un **ROI de campaña del +235.96%**.

## Software utilizado y Metodología
* Lenguaje y Procesamiento: Python, Pandas, NumPy.
* Modelado Predictivo: Scikit-Learn (Logistic Regression, CART, Random Forest) y XGBoost.
* Optimización de Hiperparámetros: Optuna.
* Interpretabilidad: SHAP values y Gain.
* Visualización: Matplotlib.

## Tabla de Modelos en Validación (Top 5% de clientes)

| Modelo | Clientes Contactados | Llamadas | Ventas | Precisión |
| :--- | :--- | :--- | :--- | :--- |
| Regresión Logística (Baseline) | 4521 | 226 | 133 | 58.85% |
| Árbol de Decisión | 4521 | 226 | 135 | 59.73% |
| Random Forest | 4521 | 226 | 138 | 61.06% |
| XGBoost (Modelo Final) | 4521 | 226 | 142 | 62.83% |

## Interpretabilidad del Modelo
Para garantizar la transparencia del algoritmo, se implementó un análisis de las variables predictoras:
* Feature Importance (Gain): Análisis de la ganancia de información para aislar las variables con efecto real en la decisión del modelo.
* SHAP Values: Evaluación del impacto para comprender cómo características específicas del perfil del cliente afectan a la probabilidad final de conversión.

## Instrucciones de Ejecución
1. Clonar el repositorio: `git clone https://github.com/DanSanchezB/Bank-Marketing-ROI-Prediction.git`
2. Instalar dependencias: `pip install -r requirements.txt`
3. Ejecutar el cuaderno principal: `proyecto_bank_marketing.ipynb` (Aviso: la celda de optimización con Optuna puede tardar en torno a 45 minutos en ejecutarse dependiendo del hardware).

