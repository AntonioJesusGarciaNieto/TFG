# Análisis de "Diagnosis of skin diseases using Convolutional Neural Networks"
El análisis de este paper[1] estará dividido en los siguientes apartados:
 - Motivación
 - Dominio del problema
 - Metodología
 - Resultados
 - Conclusión

## Motivación
En este paper se centra en el estudio de tecnicas que permitan mejorar la eficiencia y precisión de sistemas de apoyo a la toma de decisiones médicas en cuestiones de lesiones de piel.

## Dominio del problema
En este caso el dominio del problema es la clasificación binaria (bening nevi y malignant melanoma) de lesiones de piel y la posterior clasificación de los casos negativos. Se ha utilizado el conjunto de datos Dermnet.

No se especifica si han seleccionado todo el data set, pero si que se ha realizado data augmentation.

## Metodología
Antes de describir el modelo se mencionarán en una serie de fases:
 - Adquisición de imágenes. Se recojen las imágenes desde cámaras o servicios externos.
 - Pre-procesado. Se elimina el ruido de la imágen, pigmentos de la piel... Además se realiza un ajuste de tamaño.
 - Creación de componentes de almacenamientos de datos.
 - Clasificación. Mediante softmax

Por otro lado la arquitectura del modelo esta compuesta por varios bloques:
 - Unidad de eliminación del ruido (UER).
 - Unidad de resaltado y segmentación (URS).
 - Unidad de extracción de características (UEC).
 - Unidad de detección de enfermedades de piel (UDEP).
 - Unidad de entrada de atributos (UEA). En ella entran atributos como la asimetría, el contorno, el color, el diametro ...
 - Motor de clasificación (MC).

Se adjunta imagen de la arquitectura.

## Resultados
Según el estudio el rendimiento del modelo ha sido del 70%, pero podría llegar al 90% con un mayor número de imágenes.

## Conclusión
A titulo personal catalogo el estudio como interesante, pues propone el uso de bases de datos para solventar problemas de escasez de RAM, pero también encuentro algunos problemas como son:
 - La arquitectura usada es opaca, es imposible realizar o contrastar el estudio sin más información.
 - Los resultados obtenidos no son contrastables, ni se explica si se han obtenido de una forma que asegure la robusted.

## Bibliografía
[1]-Jainesh Rathod, Vishal Waghmode, Aniruddh Sodha, Dr. Prasenjit Bhavathankar-Department Of Information Technology, Sardar Patel Institute Of Technology, Mumbai 





