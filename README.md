<img width="921" height="269" alt="image" src="https://github.com/user-attachments/assets/f16e8db4-8da9-4f2f-bd3b-93366091b19f" />


# Análisis de Rentabilidad de Planes Tarifarios – Megaline

## Problema
La empresa de telecomunicaciones **Megaline** ofrece dos planes de tarifas: **Surf** y **Ultimate**. El departamento de comercialización busca identificar cuál de los dos planes genera mayores ingresos para ajustar el presupuesto de publicidad y optimizar la estrategia comercial.  
El objetivo de este proyecto es realizar un **Análisis Exploratorio de Datos (EDA)** y una **Prueba de Hipótesis Estadísticas** rigurosa para determinar la rentabilidad real de cada plan y analizar las diferencias regionales en la facturación.

---

## Datos
El análisis se basa en un dataset compuesto por 5 tablas interrelacionadas con el comportamiento mensual de 500 usuarios durante 2018:

- **Planes:** tarifa base, minutos, SMS y GB incluidos, más los costos por exceso  
- **Usuarios:** datos demográficos, ciudad de residencia y plan suscrito  
- **Llamadas, Mensajes y Consumo de Internet:** registros detallados de cada transacción  

Los datos requirieron agregación mensual por usuario para calcular el consumo total y determinar el **ingreso mensual final** combinando la tarifa fija con los costos por excesos de consumo.

---

## Enfoque
El proyecto siguió un flujo estructurado de análisis de datos y validación estadística:

- Limpieza y preprocesamiento de datos  
- Análisis Exploratorio de Datos (EDA)  
- Evaluación previa de homocedasticidad mediante la **Prueba de Levene** (`scipy.stats.levene`)  
- Selección dinámica del parámetro `equal_var` para automatizar la ejecución entre la **Prueba t de Student estándar** y la **Prueba t de Welch**  

Se evaluaron dos hipótesis principales ($\alpha = 0.05$):

- **Hipótesis 1:** Comparación de ingresos promedio entre el plan **Surf** y el plan **Ultimate**  
- **Hipótesis 2:** Comparación de ingresos promedio entre los usuarios de la región metropolitana de **NY-NJ** y el resto de las regiones  

---

## Resultados
La prueba automatizada de supuestos y pruebas t arrojó los siguientes hallazgos estadísticos:

- **Plan Ultimate:** $72.31$ USD de ingreso promedio mensual y varianza muy baja ($Var = 129.85$), comportándose como una fuente de ingresos constante y predecible  
- **Plan Surf:** $60.71$ USD de ingreso promedio mensual; aunque inicia en una cuota base de $20$ USD, más del 50% de las facturaciones incluyen excesos por GB de internet, generando una alta volatilidad ($Var = 3067.84$)  
- **Hipótesis 1 (Surf vs. Ultimate):** Prueba de Levene confirmó heterocedasticidad ($p = 5.03 \times 10^{-83}$), activando la **Prueba t de Welch**. Se rechazó $H_0$ ($t = -7.9521$, $p = 3.17 \times 10^{-15}$), demostrando que el plan Ultimate genera ingresos promedio significativamente superiores  
- **Hipótesis 2 (NY-NJ vs. Otras Regiones):** Prueba de Levene confirmó homocedasticidad ($p = 0.1258$), activando la **Prueba t estándar**. Se rechazó $H_0$ ($t = -2.0194$, $p = 0.04356$), confirmando diferencias estadísticamente significativas en la facturación del área metropolitana de NY-NJ respecto al resto del país  

---

## Conclusión
El plan **Ultimate** demostró ser la opción comercialmente más rentable para Megaline. Aunque los clientes del plan Surf pagan frecuentemente penalizaciones por consumo adicional de datos, el plan Ultimate asegura un retorno promedio más elevado por usuario ($72.31$ USD vs. $60.71$ USD) con un flujo de caja predecible y variabilidad casi nula.

Además, el comportamiento diferenciado de la región metropolitana de NY-NJ justifica la implementación de campañas de marketing regionalizadas.

---

## Herramientas y Tecnologías
- Python  
- Pandas  
- NumPy  
- SciPy (`stats.levene` y `stats.ttest_ind`)  
- Matplotlib  
- Seaborn  

---

## Conclusión Clave
Este proyecto demuestra cómo combinar el procesamiento de datos a gran escala con un pipeline automatizado de pruebas estadísticas para respaldar decisiones estratégicas de marketing con rigor matemático.



---



# Tarif Plan Profitability Analysis – Megaline

## Problem
Telecommunications company **Megaline** offers two prepaid plans: **Surf** and **Ultimate**. The commercial department needs to identify which plan generates higher revenue in order to optimize the advertising budget and adjust marketing strategy.  
The objective of this project is to perform an **Exploratory Data Analysis (EDA)** and a rigorous **Statistical Hypothesis Testing** workflow to determine the true profitability of each plan and analyze regional revenue differences.

---

## Data
The analysis is based on a dataset comprising 5 interconnected tables tracking the monthly activity of 500 users throughout 2018:

- **Plans:** base monthly fee, included minutes, SMS, and GB, plus excess usage charges  
- **Users:** demographic data, city of residence, and subscribed plan  
- **Calls, Messages, and Internet Usage:** granular logs of every single transaction  

Data required monthly aggregation per user to compute total usage and calculate the **final monthly revenue** by combining the flat base fee with overage charges.

---

## Approach
The project followed a structured data analytics and statistical verification workflow:

- Data cleaning and preprocessing  
- Exploratory Data Analysis (EDA)  
- Variance homogeneity testing using **Levene’s Test** (`scipy.stats.levene`)  
- Dynamic assignment of the `equal_var` parameter to automatically route execution between **Standard Student’s t-test** and **Welch’s t-test**  

Two main hypotheses were evaluated ($\alpha = 0.05$):

- **Hypothesis 1:** Revenue comparison between the **Surf** plan and the **Ultimate** plan  
- **Hypothesis 2:** Revenue comparison between users in the **NY-NJ** metropolitan area versus other regions  

---

## Results
The automated assumption check and t-test execution yielded the following statistical results:

- **Ultimate Plan:** $72.31$ USD average monthly revenue with very low variance ($Var = 129.85$), acting as a stable and predictable revenue stream  
- **Surf Plan:** $60.71$ USD average monthly revenue; starting at a $20$ USD base fee, over 50% of billings incurred extra data charges, driving high volatility ($Var = 3067.84$)  
- **Hypothesis 1 (Surf vs. Ultimate):** Levene’s test confirmed heteroscedasticity ($p = 5.03 \times 10^{-83}$), triggering **Welch’s t-test**. Rejected $H_0$ ($t = -7.9521$, $p = 3.17 \times 10^{-15}$), proving Ultimate generates statistically higher average revenue  
- **Hypothesis 2 (NY-NJ vs. Other Regions):** Levene’s test confirmed homoscedasticity ($p = 0.1258$), triggering **Standard t-test**. Rejected $H_0$ ($t = -2.0194$, $p = 0.04356$), confirming significant revenue differences in the NY-NJ area compared to other regions  

---

## Conclusion
The **Ultimate** plan proved to be the more profitable option for Megaline. Although Surf customers frequently pay penalties for extra data consumption, Ultimate guarantees a higher average return per user ($72.31$ USD vs. $60.71$ USD) alongside a predictable cash flow with minimal volatility.

Additionally, the distinct behavior observed in the NY-NJ region justifies targeted, region-specific marketing strategies.

---

## Tools and Technologies
- Python  
- Pandas  
- NumPy  
- SciPy (`stats.levene` and `stats.ttest_ind`)  
- Matplotlib  
- Seaborn  

---

## Key Takeaway
This project demonstrates how to combine large-scale data processing with an automated statistical hypothesis testing pipeline to support commercial decision-making with mathematical rigor.
