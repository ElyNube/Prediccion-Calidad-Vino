# Análisis de Factores de Calidad del Vino y Optimización de Modelos Predictivos
## 📌Objetivo del Proyecto y Visión de Negocio
El objetivo de este análisis es identificar qué variables físico-químicas tienen el mayor impacto en la calidad final del vino rojo. Desde una perspectiva estratégica, este modelo permite a los productores vitivinícolas enfocar sus recursos en las métricas críticas durante el proceso de fermentación, maximizando la rentabilidad del producto final mediante decisiones basadas en datos empíricos.

## 🛠️Herramientas y Metodologías
Lenguaje y Librerías: Python, Pandas, Matplotlib, Seaborn.

Técnicas de Optimización: Descenso de Gradiente, Análisis de Propiedades Matriciales.

Modelado y Regularización: Mínimos Cuadrados (OLS), Regresión Ridge (L2) y Regresión Lasso (L1).

Reducción de Dimensionalidad: Análisis de Componentes Principales (PCA).

## 📊 Fases del Análisis y Hallazgos Principales

1. Selección de Variables y Comportamiento del Producto
Tras un análisis de correlación para evitar el sobreajuste y la redundancia, el problema se redujo a cuatro variables predictoras clave:

* Alcohol (0.48): Representa la correlación positiva más fuerte, indicando que vinos con mayor graduación tienden a recibir mejores puntuaciones de calidad.
* Acidez Volátil (-0.39): Presenta una correlación negativa moderada, ya que niveles altos otorgan un sabor avinagrado que reduce drásticamente la calidad percibida. 
* Sulfatos (0.25) y Ácido Cítrico (0.23): Tienen una influencia positiva al actuar como conservantes y aportar frescura.

2. Optimización Numérica y Estabilidad del Modelo

Se demostró la viabilidad matemática del modelo al confirmar que la matriz de diseño era invertible, con un determinante mayor a cero y rango completo. 
Se implementó un algoritmo de descenso de gradiente que logró una convergencia exitosa y estable hacia el mínimo global (MSE 0.4538) utilizando una tasa de aprendizaje óptima de 0.01.

3. Evaluación de Regularización (El costo de la simplificación)
Se compararon distintas técnicas de penalización para evaluar su impacto en el negocio:

Lasso (L1): Actuó como un filtro extremo, reduciendo el coeficiente del ácido cítrico exactamente a cero. Esto ofrece un modelo altamente simplificado donde solo se necesitan medir tres químicos en laboratorio, a costa de una pérdida insignificante de precisión predictiva. 

Ridge (L2): Mantuvo las cuatro variables reduciendo levemente la magnitud de los coeficientes. Se posicionó como el equilibrio óptimo al mejorar la estabilidad numérica y lograr un MSE de 0.41379, manteniendo intacta la interpretabilidad de cada variable química.

4. El Impacto de PCA en la Toma de Decisiones

Se evaluó la aplicación de PCA para resolver posibles problemas de colinealidad. 

Al aplicar el criterio del 90% de varianza explicada, el algoritmo obligó a retener los 4 componentes principales, ya que los primeros tres solo sumaban un 89.06% de la varianza.  

Conclusión crítica: Desde la perspectiva operativa, la aplicación de PCA en este conjunto específico destruyó la interpretabilidad directa de los factores químicos sin aportar ventaja predictiva ni computacional, convirtiendo el modelo en una caja negra para el área de enología.

## 💡 Decisión Final Recomendada
Se recomienda la implementación del modelo de Regresión Ridge (L2). Este modelo demostró ser la estrategia más sólida al equilibrar un alto poder predictivo con la estabilidad matemática necesaria frente a nuevos datos ruidosos, preservando al mismo tiempo la interpretabilidad requerida por el negocio para explicar el efecto directo del alcohol y la acidez en la calidad del vino.








