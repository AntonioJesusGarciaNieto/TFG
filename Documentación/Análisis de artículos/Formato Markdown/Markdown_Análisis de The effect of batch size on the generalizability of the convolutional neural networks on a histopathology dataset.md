# Análisis de "The effect of batch size on the generalizability of the convolutional neural networks on a histopathology dataset"

El análisis de este paper estará dividido en tres campos:
 - Motivación
 - Dominio del problema
 - Metodología
 - Resultados
 - Conclusión

## Motivación.
A pesar de la importancia de las redes neuronales convolucionales para la clasificación de imágenes, y del gran foco de atención que suponen, aún quedan problemas básicos sin ser estudiados. Ejemplo de ello son la configuración de hiperparametros, una fase fundamental para el funcionamiento óptimo de una red y a la vez bastante ignorada por los desarrolladores en general.

En este estudio los autores se centran en estudiar el comportamiento de varias redes en función del tamaño de lotes. Ciertamente muchos estudios se divergen en el tamaño optimo y estandar. Los autores proponen por tanto el estudio del tamaño de lote y a su ved del coeficiente de aprendizaje.

# Dominio del problema.
Para realizar este estudio se han tomado dos conjuntos de datos, por un lado el conjunto PatchCamelyon con 220 000 imágenes y por otro lado un conjunto de datos no expecificado de kaggle que aporta 57 458 imágenes más. Ambos conjuntos de datos estan basado en imágenes médicas, en concreto de tejidos, y categorizados de forma binaria, normal o cancer. Un detalle a tener en cuanta es que el conjunto de datos PatchCamelyon esta ligeramente desbalanceado(60% positivos y 40% negativos)

# Metodología
Debido a la complejidad que supone tratar con datos médicos se ha decidido utilizar una red preentrenada, en este caso la red VGG-16. Se ha fijado el tamaño de las imágenes a 96 x 96 pixeles y se ha aplicado data augmentation tanto para corregir el desbalance como para contar con una muestra mayor de imágenes, como ya hemos visto con anterioridad el aplicar data augmentation tiene ventajas como prepara a la red contra traslacciones.

La métrica que calificará cuan bueno es el resultado para una conbinación de hiperparametros es AUC.
    
    AUC = 1/2 (TP / TN + FN + TN / TN + FP)
    
Donde:
 - TP = los casos favorables reales
 - TN = los casos negativos reales
 - FP = los casos favorables falsos
 - FN = los casos negativos falsos

Esta métrica tiene un rango entre 0,5 y 1, donde el primer extremo nos indica que la red no tiene poder predictivo alguno y el contrario que tiene un poder predictivo total.

Se probarán dos configuraciones, una con optimizador ADAM y otra con optimizador SGD
Para ambos casos se probará un tamañó de lote de 16,32,64,128 y 256 y un ratio de aprendizaje de 0.0001 y 0.001

# Resultados
Los resultado del experimento se pueden resumir en la siguiente tabla.

![Tabla de resultados](https://github.com/AntonioJesusGarciaNieto/TFG/blob/main/Img/Art%C3%ADculos/The%20effect%20of%20batch%20size%20on%20the%20generalizability%20of%20the%20convolutional%20neural%20networks%20on%20a%20histopathology%20dataset/Tabla%20de%20resultados.png)

# Conclusión

Como se puede observar en los resultados existe una cierta relacción entre el ratio de aprendizaje y el tamaño del lote con respecto a la precisión del clasificador. Los autores no recomiendan el uso de grandes lotes y recomiendan el uso extandar de lotes con un tamaño de 32, alineandose así con los resultados obtenidos en estudios como Begnio[2]. Recuerdan también que es recomendable el uso de tamaños potencia de 2 para aprobechar al máximo el la capacidad de procesamiento de las GPUs.

# Bibliografía
[1] - The effect of batch size on the generalizability of the convolutional neural networks on a histopathology dataset. Ibrahem Kandel, Mauro Castelli. Nova Information Management School (NOVA IMS), Universidade Nova de Lisboa, Campus de Campolide, 1070-312, Lisbon, Portugal.

[2] - Bengio Y. (2012) Practical Recommendations for Gradient-Based Training of Deep Architectures. In: Montavon G., Orr G.B., Müller KR. (eds) Neural Networks: Tricks of the Trade. Lecture Notes in Computer Science, vol 7700. Springer, Berlin, Heidelberg. https://doi.org/10.1007/978-3-642-35289-8_26
