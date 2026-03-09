Checklist de gobernanza

Objetivo

Este checklist resume los aspectos mínimos de gobernanza, reproducibilidad y uso responsable del proyecto de detección de objetos con YOLO11.

Datos y licencias

El origen del dataset está claramente documentado.
Se identifica el workspace, proyecto y versión del dataset.
Se verificó que el uso del dataset está permitido.
La licencia del repositorio está definida.
No se redistribuyen imágenes si la licencia no lo permite.
Se distingue entre licencia del código y licencia de los datos.

Seguridad y credenciales

No hay API keys privadas dentro del notebook.
No hay secretos expuestos en el repositorio público.
La autenticación se realiza mediante variables seguras o Colab Secrets.
Se revisó el historial del repositorio para evitar exposición de claves.
Si una clave fue expuesta, fue revocada y regenerada.

Calidad del dataset

Las clases están definidas con criterios claros de inclusión y exclusión.
Las reglas de anotación están documentadas.
Se revisó la consistencia del etiquetado.
Se detectaron posibles ejemplos ambiguos o mal anotados.
El dataset tiene una división clara entre entrenamiento, validación y prueba.

Reproducibilidad

El notebook puede ejecutarse de principio a fin.
Las dependencias están listadas en requirements.txt.
Las rutas del proyecto están documentadas.
El archivo README.md explica cómo reproducir el entrenamiento.
El modelo final y las métricas principales están incluidos o enlazados.
Se documentan hiperparámetros básicos del entrenamiento.

Evaluación y transparencia

Se incluyen métricas de precisión, recall, mAP50 y mAP50-95.
Se incluyen curvas de entrenamiento.
Se incluye matriz de confusión.
Se incluyen ejemplos de predicción.
Se documentan limitaciones del modelo.
Se describe al menos un análisis básico de errores.

Sesgo y representatividad

Se evaluó si el dataset representa distintos contextos visuales.
Se identificaron posibles sesgos por fondo, ángulo, escala o iluminación.
Se reconoce si el dataset es pequeño o poco diverso.
Se evita afirmar generalización total sin validación externa.

Uso responsable

El repositorio aclara el alcance real del modelo.
No se presentan los resultados como perfectos o universales.
Se explican riesgos de uso fuera del contexto del dataset.
Se indican recomendaciones para futuras mejoras.
Se reconoce que el modelo depende de la calidad de los datos.

Publicación en GitHub

El repositorio tiene nombre claro y estructura ordenada.
El README.md describe el proyecto, resultados y limitaciones.
La carpeta docs contiene documentación complementaria.
El repositorio no contiene archivos innecesarios o sensibles.
El notebook abre correctamente desde GitHub y Colab.

Cierre

Este checklist ayuda a que el repositorio no solo funcione técnicamente, sino que también sea más claro, más seguro y más responsable desde el punto de vista académico y profesional.
