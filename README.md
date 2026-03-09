# train_yolo11_dump_truck_colab
Ejercicio de consolidación de entrega — Prototipo AECO CV + repositorio reproducible (solo nube)

YOLO11 - Detección de Dump Truck

Repositorio reproducible para entrenar, validar e inferir un modelo de detección de objetos con YOLO11 sobre un dataset personalizado alojado en Roboflow. El flujo está preparado para ejecutarse en Google Colab y compartirse en GitHub como repositorio público.

Descripción del proyecto

El objetivo de este proyecto es entrenar un modelo YOLO11 para detectar la clase dump truck en imágenes, documentando el proceso completo de entrenamiento, validación e inferencia, junto con los artefactos necesarios para su reproducción por terceros.

Este repositorio incluye:
notebook de entrenamiento ejecutable en Google Colab
pesos del modelo entrenado
métricas de entrenamiento y validación
curvas de rendimiento
matriz de confusión
ejemplos de predicción
notas de resultados y limitaciones

Estructura del repositorio

dump-truck-yolo11-repo/
README.md
requirements.txt
.gitignore
notebooks/
train_yolo11_dump_truck_colab.ipynb
results/
best.pt
last.pt
results.csv
results.png
confusion_matrix.png
confusion_matrix_normalized.png
PR_curve.png
P_curve.png
R_curve.png
F1_curve.png
predictions/
docs/
notes.md

Dataset

Workspace: angelas-workspace-btupm
Proyecto: dump-truck-co7as
Versión: 1
Formato: yolov11

El dataset se descarga directamente desde Roboflow dentro del notebook, por lo que no es necesario almacenar localmente todas las imágenes dentro del repositorio.

Requisitos

cuenta de GitHub
cuenta de Roboflow con acceso al dataset
Google Colab
GPU activada en Colab
secret configurado en Colab con el nombre: ROBOFLOW_API_KEY

Cómo ejecutar el proyecto

1. Abrir el notebook notebooks/train_yolo11_dump_truck_colab.ipynb en Google Colab.
2. Activar GPU en el entorno de ejecución.
3. Crear el secret ROBOFLOW_API_KEY en Colab.
4. Ejecutar todas las celdas en orden.
5. Revisar los resultados guardados en la carpeta results/.

Resultados del entrenamiento

El modelo fue entrenado durante 50 épocas y alcanzó los siguientes resultados finales en validación:

Precisión final: 0.99091
Recall final: 1.00000
mAP50 final: 0.99500
mAP50-95 final: 0.80559

Interpretación técnica de los resultados

Los resultados muestran un desempeño muy alto del modelo en la detección de la clase objetivo. La precisión final de 0.99091 indica que la gran mayoría de las detecciones positivas realizadas por el modelo fueron correctas. El recall de 1.00000 sugiere que, en el conjunto de validación, el modelo logró recuperar todos los objetos esperados de la clase analizada.

El valor de mAP50 = 0.99500 refleja un comportamiento sobresaliente bajo un criterio de coincidencia IoU menos estricto, lo cual indica que el modelo identifica con gran eficacia la presencia del objeto. Por su parte, el valor de mAP50-95 = 0.80559 muestra que el rendimiento sigue siendo sólido bajo umbrales más exigentes, aunque todavía existe margen de mejora en la precisión espacial de las cajas delimitadoras.

En conjunto, las curvas de entrenamiento y validación sugieren una convergencia estable del modelo. Las pérdidas de entrenamiento descienden progresivamente, mientras que las métricas de validación mantienen una tendencia favorable. Esto respalda la idea de que el modelo aprendió patrones relevantes del dataset y alcanzó una capacidad adecuada de generalización dentro del conjunto evaluado.

Notas de resultados

El modelo mostró un comportamiento robusto durante el entrenamiento, con una reducción progresiva de las pérdidas train/box_loss, train/cls_loss y train/dfl_loss. Esta tendencia indica que el proceso de ajuste fue estable y que el modelo fue aprendiendo a localizar y clasificar correctamente la clase objetivo.

Las métricas de validación se mantuvieron en niveles altos durante las últimas épocas, especialmente en precisión, recall y mAP50. Esto sugiere que el modelo no solo aprendió a detectar el objeto, sino que también mantuvo un rendimiento consistente en el conjunto de validación.

El valor de mAP50-95 es menor que el de mAP50, lo cual es completamente esperable, ya que evalúa el modelo bajo condiciones más estrictas de intersección sobre unión. Aun así, el resultado obtenido sigue siendo alto y respalda la utilidad del modelo para tareas de detección de objetos en este contexto.

La matriz de confusión, junto con las imágenes de predicción, permite complementar las métricas numéricas con evidencia visual. Esto resulta útil para verificar si los aciertos y errores del modelo están vinculados a factores como el tamaño del objeto, el ángulo de captura, la iluminación, la complejidad del fondo o la calidad de las anotaciones.

Limitaciones del modelo

Aunque los resultados son muy favorables, este modelo presenta varias limitaciones que deben ser reconocidas antes de considerarlo como una solución completamente generalizable.

1. Dependencia del dataset
   El rendimiento del modelo depende directamente de la calidad, cantidad y diversidad del dataset utilizado. Si las imágenes del conjunto de entrenamiento y validación son demasiado homogéneas, el modelo puede comportarse muy bien en ese entorno pero perder capacidad de generalización en escenarios distintos.

2. Riesgo de sobreajuste contextual
   Un recall perfecto y una precisión muy alta son indicadores positivos, pero también obligan a examinar con cautela si el conjunto de validación es suficientemente desafiante e independiente del entrenamiento. Si existe demasiada similitud entre ambos subconjuntos, el desempeño real fuera del dataset puede ser menor.

3. Limitación del mAP50-95 frente al mAP50
   Aunque el modelo alcanza un mAP50 extremadamente alto, el mAP50-95 es más exigente y revela que todavía hay margen de mejora en la precisión exacta de las cajas. Esto significa que el modelo detecta correctamente el objeto, pero puede seguir mejorando en la localización fina de sus bordes.

4. Sensibilidad a escenas complejas
   El modelo puede presentar errores en escenas con oclusiones, múltiples vehículos, fondos visualmente saturados, objetos parcialmente visibles, baja resolución o condiciones de iluminación no representadas adecuadamente en el dataset.

5. Dependencia de la calidad del etiquetado
   Si existen cajas mal ajustadas, anotaciones inconsistentes o errores humanos en el etiquetado, las métricas pueden verse afectadas. Incluso un modelo con buenos resultados puede estar condicionado por la calidad de las etiquetas de origen.

6. Evaluación centrada en un solo entorno de datos
   El modelo ha sido validado principalmente dentro del mismo ecosistema de datos desde el que fue entrenado. Para confirmar su robustez, sería recomendable probarlo con imágenes externas no vistas previamente y con condiciones de captura diferentes.

7. Ausencia de análisis detallado por tipo de error
   Las métricas globales resumen bien el rendimiento general, pero no sustituyen un análisis cualitativo de falsos positivos y falsos negativos. Este análisis sigue siendo necesario para comprender mejor en qué situaciones concretas el modelo puede fallar.

Recomendaciones de mejora

aumentar la diversidad del dataset con más escenarios, ángulos y condiciones de iluminación
revisar visualmente la calidad de las anotaciones
evaluar el modelo con imágenes externas no utilizadas en entrenamiento
comparar variantes como yolo11n, yolo11s o superiores
documentar falsos positivos y falsos negativos
incorporar un conjunto de prueba independiente
ampliar el análisis visual de la matriz de confusión y las predicciones

Reproducibilidad

Este repositorio fue estructurado para que un tercero pueda abrir el notebook en Google Colab y reproducir el flujo de trabajo sin instalaciones locales complejas. No obstante, para ejecutar el entrenamiento completo se requiere acceso válido al dataset y configuración del secret ROBOFLOW_API_KEY.

Nota de seguridad

Este repositorio no incluye claves privadas de Roboflow. Las credenciales deben almacenarse únicamente en los secretos de Google Colab o variables de entorno seguras.

Archivos de salida relevantes

Dentro de results/ se pueden encontrar los artefactos principales del experimento:

best.pt: mejor modelo entrenado
last.pt: último checkpoint
results.csv: métricas por época
results.png: resumen gráfico del entrenamiento
confusion_matrix.png: matriz de confusión
confusion_matrix_normalized.png: matriz normalizada
PR_curve.png, P_curve.png, R_curve.png, F1_curve.png: curvas de evaluación
predictions/: ejemplos de inferencia

Autoría

Proyecto preparado para documentación, entrenamiento y publicación reproducible en GitHub sobre detección de objetos con YOLO11.

Licencia

 MIT License
