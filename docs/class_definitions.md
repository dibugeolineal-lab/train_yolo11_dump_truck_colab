Definiciones de clases

Clase principal

dump truck

Vehículo pesado de carga utilizado para transportar materiales sueltos como tierra, grava, arena, escombros o rocas. Se caracteriza por tener una caja o tolva trasera basculante diseñada para descargar el material por inclinación.

Criterios de inclusión

Se debe etiquetar como dump truck cuando el vehículo corresponde claramente a un camión volquete o camión de volteo, la cabina y la caja de carga basculante son visibles total o parcialmente, el objeto aparece completo o parcialmente ocluido pero sigue siendo reconocible, la imagen muestra el vehículo desde frente, perfil, parte trasera o ángulo oblicuo, o el vehículo está estacionado, en movimiento, cargado o descargando material.

Criterios de exclusión

No se debe etiquetar como dump truck cuando el vehículo no tiene una tolva o caja basculante identificable, se trata de otro tipo de camión de carga sin sistema de volcado, el objeto es demasiado pequeño o borroso y no puede identificarse con seguridad, solo se observa una parte mínima del vehículo sin evidencia suficiente para confirmar la clase, o la imagen contiene maquinaria pesada distinta, como excavadoras, retroexcavadoras, cargadores frontales o tractores.

Reglas de anotación

Dibujar la caja delimitadora alrededor de todo el vehículo visible. Incluir cabina, chasis y tolva visible dentro de la misma caja. Evitar cajas demasiado amplias con mucho fondo innecesario. Evitar cajas demasiado ajustadas que corten partes visibles del vehículo. En caso de oclusión, anotar solo si la clase sigue siendo claramente identificable. Si hay múltiples dump trucks en una imagen, anotar cada uno por separado.

Casos ambiguos

Vehículo parcialmente visible. Se anota si todavía es posible reconocer con suficiente claridad que se trata de un dump truck.

Vehículo muy lejano. Se anota solo si conserva rasgos visuales suficientes para diferenciarlo de otros camiones.

Imagen borrosa. No se anota si la baja calidad impide confirmar la clase con seguridad.

Observación general

La consistencia en estas definiciones es clave para mejorar la calidad del dataset, reducir errores de etiquetado y aumentar la confiabilidad del modelo entrenado.

ARCHIVO: docs/error_analysis.md

Análisis de errores del modelo

Objetivo

Este documento resume los principales tipos de error observados o esperados durante la evaluación del modelo YOLO11 entrenado para detectar la clase dump truck.

Tipos de error

Falsos positivos

Ocurren cuando el modelo detecta un dump truck en una imagen donde realmente no existe uno.

Posibles causas

Confusión con otros camiones de carga. Similitud visual con vehículos pesados no etiquetados como dump truck. Fondos industriales o de construcción con formas parecidas. Sobreajuste a patrones específicos del dataset.

Falsos negativos

Ocurren cuando sí hay un dump truck en la imagen, pero el modelo no lo detecta.

Posibles causas

Objeto demasiado pequeño. Oclusión parcial. Baja iluminación. Ángulos poco frecuentes. Imágenes borrosas o de baja resolución. Insuficiente diversidad en el dataset de entrenamiento.

Localización imprecisa

Ocurre cuando el modelo detecta correctamente el objeto, pero la caja delimitadora no ajusta con suficiente precisión.

Posibles causas

Anotaciones de entrenamiento inconsistentes. Bordes poco claros del vehículo. Escenas complejas con superposición de objetos. Limitaciones del modelo bajo umbrales IoU más exigentes.

Observaciones de rendimiento

El modelo alcanzó métricas altas en precisión, recall y mAP50, lo que indica un desempeño fuerte sobre el conjunto de validación. Sin embargo, la diferencia entre mAP50 y mAP50-95 sugiere que todavía existe margen de mejora en la localización precisa de las cajas delimitadoras.

La matriz de confusión y las imágenes de predicción deben revisarse conjuntamente para identificar si los errores se concentran en ciertos contextos, por ejemplo objetos pequeños, fondos complejos, escenas con varios vehículos, oclusiones, diferencias de iluminación y cambios de perspectiva.

Riesgos de interpretación

Un desempeño alto en validación no garantiza por sí solo una generalización robusta en entornos nuevos. Si el conjunto de validación es pequeño o muy similar al de entrenamiento, las métricas pueden sobreestimar la capacidad real del modelo.

Recomendaciones de mejora

Ampliar la diversidad del dataset. Incluir más imágenes con distintos ángulos, distancias e iluminaciones. Revisar la consistencia del etiquetado. Probar el modelo con imágenes externas no vistas. Documentar ejemplos concretos de falsos positivos y falsos negativos. Comparar distintas variantes del modelo YOLO11. Realizar análisis cualitativo de predicciones difíciles.

Conclusión

El modelo presenta resultados prometedores para la detección de dump truck, pero su robustez debe seguir evaluándose con evidencia visual y conjuntos de datos más diversos para confirmar su capacidad de generalización.
