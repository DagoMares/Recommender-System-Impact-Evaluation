# Recommender System Impact Evaluation: A/B Test Analysis 🧪📈

**Evaluación de impacto de un nuevo sistema de recomendaciones en la tasa de conversión de usuarios de la UE.**

[![Status](https://img.shields.io/badge/status-completed-red.svg)]()
[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![Analysis](https://img.shields.io/badge/Method-Z--Test-green.svg)]()

## 📋 Tabla de Contenidos
- [Contexto del Proyecto](#-contexto-del-proyecto)
- [Objetivos](#-objetivos)
- [Metodología](#-metodología)
- [Análisis Exploratorio (EDA)](#-análisis-exploratorio-eda)
- [Resultados de la Prueba A/B](#-resultados-de-la-prueba-ab)
- [Conclusiones y Recomendaciones](#-conclusiones-y-recomendaciones)
- [Tecnologías Utilizadas](#-tecnologías-utilizadas)

---

## 🏢 Contexto del Proyecto
Se llevó a cabo una prueba A/B para evaluar la efectividad de un **nuevo sistema de recomendaciones** mejorado. El experimento se centró en usuarios de la Unión Europea, dividiéndolos en dos grupos:
* **Grupo A (Control):** Sistema actual.
* **Grupo B (Experimental):** Nuevo sistema de recomendaciones.

Se recolectaron datos de comportamiento (eventos), datos de marketing y registros de nuevos usuarios para el análisis.

## 🎯 Objetivos
El objetivo principal del estudio fue validar la siguiente hipótesis de negocio:
> **"El nuevo sistema de recomendaciones generará un aumento del 10% en la tasa de conversión en cada etapa del embudo de ventas (product_page → product_cart → purchase)."**

## ⚙️ Metodología
El análisis siguió un flujo de trabajo riguroso:

1.  **Preprocesamiento de Datos**:
    * Estandarización de nombres de columnas y conversión de tipos de datos (`datetime`).
    * Filtrado de usuarios según región (UE) y prueba específica (`recommender_system_test`).
    * Verificación de la integridad de los datos (duplicados, usuarios en ambos grupos).
2.  **Análisis de Embudo (Funnel Analysis)**:
    * Cálculo de tasas de conversión totales y relativas por etapa.
3.  **Análisis Exploratorio (EDA)**:
    * Distribución temporal de eventos para detectar anomalías o estacionalidad.
    * Comparación de la frecuencia de eventos por usuario entre grupos.
4.  **Prueba de Hipótesis (A/B Testing)**:
    * Aplicación de la **Prueba Z para diferencia de proporciones**.
    * Hipótesis Nula ($H_0$): $p_B - p_A \le 0.1$ (El aumento es menor o igual al 10%).
    * Nivel de significancia ($\alpha$): 0.05.

## 📊 Análisis Exploratorio (EDA)
Durante la exploración de datos se detectaron hallazgos clave:
* **Anomalía Temporal:** Se identificó un pico inusual de actividad en el Grupo A entre el 13 y el 23 de diciembre, no asociado directamente a eventos de marketing registrados.
* **Disparidad en *Engagement*:** El Grupo A mostró una media de eventos por usuario significativamente mayor (6.78) que el Grupo B (5.70), confirmado mediante prueba de Levene y T-test.
* **Inconsistencia de Datos:** Se detectó un problema de calidad de datos en la etapa `product_cart`, donde las conversiones aparentes superan el 100% hacia `purchase` en ciertos casos, sugiriendo fallos en el trackeo de eventos intermedios.

## 🧪 Resultados de la Prueba A/B
Los resultados estadísticos de las Pruebas Z para cada etapa del embudo fueron contundentes:

| Etapa del Embudo | Estadístico Z | Valor-p | Resultado |
| :--- | :--- | :--- | :--- |
| **Product Page** | -9.63 | 1.0 | **No se rechaza H0** |
| **Product Cart** | -6.93 | 1.0 | **No se rechaza H0** |
| **Purchase** | -7.65 | 1.0 | **No se rechaza H0** |

*Nota: Un valor-p de 1.0 en una prueba de cola derecha indica que la diferencia observada es negativa o nula, muy lejos del aumento esperado del 10%.*

## 🚀 Conclusiones y Recomendaciones

1.  **Rechazo de la Hipótesis de Negocio:** No existe evidencia estadística que respalde que el nuevo sistema de recomendaciones aumente la conversión en un 10%. De hecho, los datos sugieren un desempeño inferior al sistema actual.
2.  **No Implementación:** Se recomienda **no desplegar el nuevo sistema** en producción en su estado actual.
3.  **Auditoría de Datos:** Es crítico revisar la implementación técnica del trackeo de eventos, especialmente en el evento `product_cart`, para asegurar la fiabilidad de futuros experimentos.
4.  **Investigación de Anomalías:** Se sugiere investigar el pico de tráfico del 13-23 de diciembre en el grupo de control para descartar factores externos que hayan podido sesgar la prueba.

## 💻 Tecnologías Utilizadas
* **Python**: Análisis y procesamiento de datos.
* **Pandas**: Manipulación de DataFrames.
* **SciPy**: Pruebas estadísticas (Z-test, T-test, Levene).
* **Matplotlib / Seaborn**: Visualización de datos y distribuciones.

---
*Autor: [Dagoberto Mares](https://github.com/DagoMares)*

*Contacto: [![Gmail Badge](https://img.shields.io/badge/-dagobertomares0@gmail.com-c14438?style=flat&logo=Gmail&logoColor=white&link=mailto:dagobertomares0@gmail.com)](mailto:dagobertomares0@gmail.com) - 
[![Linkedin Badge](https://img.shields.io/badge/-dagobertomares-0072b1?style=flat&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/dagoberto-mares/)](https://www.linkedin.com/in/dagoberto-mares/)*
