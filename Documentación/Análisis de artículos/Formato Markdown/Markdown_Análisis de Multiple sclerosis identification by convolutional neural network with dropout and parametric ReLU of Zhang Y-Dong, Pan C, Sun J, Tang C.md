## En el siguiente texto pasaré a condensar la información contenida en el artículo: "Multiple sclerosis identification by convolutional neural network with dropout and parametric ReLU"[1].

Segmentaré este análisis personal en tres campos: 
- Resumen. 
- Opinión.
- Bibliografía

El resumen estará sub dividido en:
- Dominio del problema y objetivo.
- Pre-procesado de imágenes.
- Metodología.
- Conclusión

### Resumen.

#### Dominio del problema y objetivo.
En este artículo se pretende crear una red que sirva de apoyo al diagnostico precoz de casos de esclerosis, para ello se contará con 676 imágenes diagnosticada como sclerosis y 681 diagnosticado como sano.
El objetivo es probar los conceptos de data augmentation,PReLU[2] y dropout para optimizar la red.

#### Pre-procesado de imágenes.
El set de datos con el que se trabaja pertenece de diversas fuentes, y las imágenes se han tomado usando diferentes técnicas.
Los autores recurren a la normalización mediante el método de "diagram stretching[3]"
Los datos se reparten en tres grupos, entrenamiento,validación y test usando el método de "hold-out".
Debido a la falta de una cantidad de datos suficiente se utiliza la técnica de "data augmentation"[4]. Se aplican 5 modificadores[5].
- Rotación.
- Variación del valor gamma.
- Inyección de ruido.
- Translaciones aleatorias.
- Escalado.
La aplicación de esta técnica aumenta el número de imágenes en 150 por cada imagen original.

#### Metodología.
La red que se estudiará será una red profunda convolucional de 10 capas, 7 capas de convolución y 3 capas totalmente conectadas (las capas de dropout serán 0.4,0.5,0.5).
La estructura de las capas convolucionales es : capa convolucional, PReLU y capa de pooling.
En el estudio se explica como han seleccionado el tamaño de la red.

#### Conclusión.
El dropout incrementó la precisión en 0.88 %.
El uso de la PReLU incrementó la precisión en 1.92 % comparándalo con ReLU.
El uso de la PReLU incrementó la precisión en 1.48 % comparándalo con ReLU. 
			
### Opinión.
Este proyecto aporta una información muy valiosa, pues confirma que la implementación de técnicas sencillas permite un incremento notable en la precisión.

### Bibliografía

[1] - Zhang Y-Dong, Pan C, Sun J, Tang C, Multiple sclerosis
identification by convolutional neural network with dropout and parametric ReLU,
Journal of Computational Science (2018), https://doi.org/10.1016/j.jocs.2018.07.003

[2] - He, K.M., et al. Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification. in IEEE International 

[3] - Kim, D., Contrast Enhancement Scheme using Histogram Stretching and Equalization on Singular Value Domain. Information, 2017. 20(2B):
p. 1221

[4] - Touloupou, P., et al., Efficient Model Comparison Techniques for Models Requiring Large Scale Data Augmentation. Bayesian Analysis,
2018. 13(2): p. 437-459

[5] - Lv, Y.-D., Alcoholism detection by data augmentation and convolutional neural network with stochastic pooling. Journal of Medical Systems,
2018. 42(1): Article ID. 2