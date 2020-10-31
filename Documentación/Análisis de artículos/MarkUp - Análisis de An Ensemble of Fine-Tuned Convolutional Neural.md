## En el siguiente texto pasaré a condensar la información contenida en el artículo: "An Ensemble of Fine-Tuned Convolutional Neural Networks for Medical Image Classification"[1].

Segmentaré este análisis personal en tres campos: 
- Type some Markdown on the left
- See HTML in the right
- Magic

El resumen estará sub dividido en:
- Dominio del problema y objetivo.
- Pre-procesado de imágenes.
- Metodología.

# Resumen.

### Dominio del problema y objetivo.
En este artículo se pretende crear un ensamblaje de redes convolucionales para poder clasificar la modalidad de diferentes imágenes médicas.
El objetivo es probar los conceptos de "ensemble learning" y "fine-tuning".
Las redes serán pre-entrenadas con algo más de 1 M de imágenes y serán entrenadas con aproximadamente 1100 (pertenecientes al Subfigure Classification dataset de la colección pública de ImageCLEF 2016).

### Pre-procesado de imágenes.
Debido a la falta de una cantidad de datos suficiente se utiliza la técnica de "data augmentation". Se aplican el método 10-fold, que consiste en:

- Ajustar la dimensión de los cortes a la de la entrada de la arquitectura.
- Generar 5 imágenes nuevas a partir de cortes de cada imagen. Esquinas y centro.
- Generar 5 imágenes nuevas a partir de rotaciones sobre el eje X.

La aplicación de esta técnica aumenta el número de imágenes en 10 por cada imagen original.
De todas las imágenes obtenidas se hace una separación aleatoria 90 a 10 para separar los conjuntos de entrenamiento y validación respectivamente.

### Metodología.
##### Detalles previos.
En el estudio se explica que las redes entrenadas con fine-tuning se pueden usar de dos maneras, usando un SVM (Support Vector Machine) y con una softmax.

En el estudio se usan dos redes convolucionales:
- Alexnet : Formada por 8 capas entrenables. 5 capas de convolución y 3 capas completamente conectada y las capas de max pooling correspondientes(después de la 1ª,2ª y 5ª capa).
- GoogLeNet : Formado por 22 capas entrenables.

Los clasificadores a usar pueden ser : 
 - softmax.
 - one-vs-one multi-class SVM. SVMs es una técnica de clasificación binaria supervisada que permite clasificar las imágenes de entrenamiento en dos categorías.
 
Para resolver el problema que nos compete (multiclase) en el artículo se propone combinar varios SVM y entrenarlos como SVM A-vs-B para el resultado de cada sub-red. Las probabilidades posteriores se estimaron basándose en la minimización de la divergencia de Kullback-Leibler basado en la salida de los SVM [2]
		
##### Ajuste fino.
Las aquitecturas usadas fueron pre-entrenadas y diseñadas para la clasificación de 1000 clases, por lo que se sustituirán las capas totalmente conectadas para que clasifiquen las clases necesarias para nuestro problema (30).
Después se procedió ha realizar la técnica de 'fine-tuning', esta consiste en tomar una red pre-entrenada y entrenarla ligeramente (todas las capas a diferencia de en la tecnica de 'transfer learning') para que se adapte mejor a nuestro problema.
En el artículo se toma como lr (ratio de aprendizaje) 5 x 10 e-6 .Basado en estudios previos [3][4][5].
Se usará un valor de momentum = 0.9 (el momentum regula la fluctuación del lr).
El termino de control de decaimiento del peso (lambda) previene un crecimiento del peso excesivo.Se dejara su valor por defecto, 1. 

##### Conclusión.
Queda demostrado que el ensablaje realizado en el articulo es mejor que cualquiera de sus subredes de forma individual ya se utilize en ella el transfer learning + SVM, fine-tuning + softmax o fine-tuning + SVM
Por otro lado dentro del estado del arte, queda en una cuarta posición. [37]
			
### Opinión.

Este articulo respalda el uso de redes paralelas que se basen en fine-tuning, y SVG. También nos propone seguir el estudio usando la arquitectura ResNet-152[7]


### Bibliografía

[1] - Ashnil Kumar, Member, IEEE, Jinman Kim, Member, IEEE ,David Lyndon, Michael Fulham, and Dagan Feng, Fellow, IEEE An Ensemble of Fine-Tuned Convolutional Neural Networks for Medical Image Classification


[2] - B. Zadrozny, “Reducing multiclass to binary by coupling probability estimates,” in Adv Neur In, 2001, pp. 1041–1048.

[3] - D. Lyndon, A. Kumar, J. Kim, P. H. W. Leong, and D. Feng, “Convolutional neural networks for medical clustering,” in CLEF 2015 Working Notes, ser. CEUR Workshop Proceedings, vol. 1391, 2015.

[4] - D. Lyndon, A. Kumar, J. Kim, P. H. W. Leong, and D. Feng, “Convolutional neural networks for medical classification,” in CLEF 2015 Working Notes, ser. CEUR Workshop Proceedings, vol. 1391, 2015.

[5] - A. Kumar, J. Kim, D. Lyndon, and D. Feng, “Subfigure and multilabel classification using a fine-tuned convolutional neural network,” in CLEF 2016 Working Notes, ser. CEUR Workshop Proceedings, vol. 1609, 2016, pp. 318–321.

[6] -  S. Koitka and C. M. Friedrich, “Traditional Feature Engineering and
Deep Learning Approaches at Medical Classification Task of ImageCLEF 2016 ,” in CLEF 2016 Working Notes, ser. CEUR Workshop Proceedings, vol. 1609, 2016, pp. 304–317.

[7] -  S. Koitka and C. M. Friedrich, “Traditional Feature Engineering and
Deep Learning Approaches at Medical Classification Task of ImageCLEF 2016 ,” in CLEF 2016 Working Notes, ser. CEUR Workshop Proceedings, vol. 1609, 2016, pp. 304–317.