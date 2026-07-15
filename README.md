# Determinación de la Carga del Electrón (Experimento de Millikan) con ML

Este proyecto presenta un pipeline de Ciencia de Datos para procesar, analizar y automatizar la cuantización de la carga eléctrica a partir de los datos del **Experimento de la Gota de Aceite de Millikan**. 

El núcleo del proyecto consiste en un enfoque híbrido que combina datos experimentales reales con datos sintéticos para robustecer estadísticamente el análisis.

## Componentes Metodológicos

* **Generación de Datos Sintéticos con Ruido Estocástico (Gaussiano):** Simulación de velocidades "ideales" perturbadas mediante una distribución normal. Esto emula la incertidumbre instrumental real (errores de cronometraje, turbulencias de aire) y expande el conjunto de datos para el entrenamiento del modelo.
* **Segmentación Inteligente (Machine Learning):** * Evaluación de densidad y separación mediante **Silhouette Score** para determinar matemáticamente el número óptimo de escalones de carga ($k$).
  * Agrupamiento con **K-Means Clustering** para asignar de forma no supervisada cada gota a su nivel de ionización (múltiplo entero de la carga $e$).
* **Regresión Lineal:** Ajuste final por mínimos cuadrados sobre los grupos identificados para extraer el valor experimental de la carga elemental ($e$).


## Conclusiones Destacadas

* **Sinergia Híbrida:** El análisis aislado de las 82 muestras de laboratorio arrojaba un error del **10.95%** debido a limitaciones en el tamaño de la muestra. La integración de los datos sintéticos actuó como un regularizador estadístico que densificó el espacio, reduciendo el error final al **0.48%**.
* **El Ruido como Incertidumbre:** El modelo demostró ser altamente sensible al ruido gaussiano. Incrementar la desviación estándar del ruido simula un entorno de menor precisión, provocando que los escalones de carga se traslapen en la fase de agrupamiento y aumentando el error de la regresión.
* **Intervención Humana + Automatización:** El pipeline utiliza un enfoque de control híbrido. El investigador mantiene el criterio para acotar visualmente el rango de búsqueda de escalones en la interfaz, mientras que el algoritmo de Machine Learning asume la tarea de segmentar, delimitar fronteras de grupo y ordenar los niveles con precisión matemática.
