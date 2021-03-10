# Análisis de "DEEMOLE: Deep Neural Networks For Skin Mole Lesion Classification"

Este paper se puede encontrar bajo la siguiente cita:
V. Pomponiu, H. Nejati, N.-M. Cheung Information System, Technology and Desing (SUTD) Singapore University of Technology and Design (ISTD) Somapah Road 8, Singapore, 487372

El análisis de este paper estará dividido en los siguientes apartados:
 - Motivación
 - Dominio del problema
 - Metodología
 - Resultados
 - Conclusión

## Motivación
En este paper se estudia uno de los problemas comunes en la clasificación de lesiones de piel, la detección de patrones. El modo en el que se enfrenta el paper a esta problemática es aplicando modelos de redes neuronales para la extracción de patrones.

## Dominio del problema
En este caso el dominio del problema es la clasificación binaria (bening nevi y malignant melanoma) de lesiones de piel. En concreto se han utilizado dos contuntos de datos:
 - DermIS que es un atlas dermatologico Europeo para los profesionales de la salud.
 - DermQuest una librería de imágenes dermatologicas.

El resultado de seleccionar imágenes de ambos conjuntos ha sido 399 imágenes en RGB con ditribución de 217 bening nevi y 182 malignant melanoma. Uno de los criterios de selección de imágenes para el conjunto de datos fue la resolución por biopsia (el método más eficaz).

## Metodología
La arquitectura de la red neuronal convolucional que se usa en este estudio no es otra que AlexNet[1]. Además, se le añaden algúnas modificaciones. A continuación se añade una imagen en la que muestra la arquitectura.

![Tabla de resultados](https://github.com/AntonioJesusGarciaNieto/TFG/blob/main/Img/Art%C3%ADculos/DEEMOLE:%20Deep%20Neural%20Networks%20For%20Skin%20Mole%20Lesion%20Classification/Screenshot_5.png)

Analizaremos cada uno de los bloques:
 - `Bloque de Data Augmentation`: Este bloque tiene como finalidad reducir el overfitting. Se realizan una serie de modificaciones como variar las bandas de color RGB, emplear reducción Gaussiana con un filtro de pasa baja, adición de ruido, ecualización del histograma... En la fase de data augmentation ha aumentado las imágenes originales (399) a 10000, es decir cada imágen general ha generado 25 nuevas.
 
 - `Bloque Clasificador`: El funcionamiento de este bloque es bastante interesante. Se utiliza la red convolucional AlexNet[1] como extractora de características y posteriormente se toman los características de las tres ultimas capas,se les agrupa y se les aplica un algoritmo de k-NN. La métrica usada en este experimento es la distancia cosenoidal puesto que es más usada y además aporta una cierta robustez adicional.

De cara a obtener unos resultados robustos el esquema de entrenamiento se ha basado en la conocida técnica de validación cruzada, en concreto el estudio ha utilizado 10 particiones.

## Resultados
Los resultados obtenidos se pueden resumir en la siguiente tabla.

![Tabla de resultados](https://github.com/AntonioJesusGarciaNieto/TFG/blob/main/Img/Art%C3%ADculos/DEEMOLE:%20Deep%20Neural%20Networks%20For%20Skin%20Mole%20Lesion%20Classification/trabla_resultados.png)

Como anotación indicar que:
 - Sens se corresponde con la sensibilidad = TP/(TP + FN)
 - Spec se corresponde con la especificidad = FN/(FN+FP)
 - Acc se corresponde con la precisión = (TP+TN)/(TP+FP)

Donde TP = Verdaderos positivos, TN = Verdaderos negativos, FP = Falsos Positivos, FN = Falsos Negativos

## Conclusión
Parece que realmente existe una mejora significativa en cada una de las mediciones, y en mi opinión parece una ruta de estudio bastante atractiva que incentiva la unión entre aprendizaje supervisado y no supervisado. No obstante, considero que el estudio tiene dos pequeñas faltas:
    - La primera, es que no se estudia la solución resultado de seguir el ciclo normal de trabajo de la arquitectura extractora de característica (AlexNet).
    - En segundo lugar, la comparación con los articulos 16[2],17[3] y 18[4] es cuestionable, pues en estos, lo que se pretende es crear modelos ligeros que sean soportados en dispositivos móviles. Sin embargo, en el paper a analizar no se hace referencia a dicha limitación. 

## Bibliografía
[1]-A. Krizhevsky et al., “Imagenet classification with deep convolutional neural networks,” in Advances in Neural Information Processing Systems 25, F. Pereira et al., Eds., pp. 1097–1105. Curran Associates, Inc., 2012.

[2] Ramlakhan K. and Y. Shang, “A mobile automated skin lesion classification system,” in ICTAI, 2011, pp. 138 – 141.

[3] Doukas Charalampos et al., “Automated skin lesion assessment using mobile technologies and cloud platforms,” in Conf Proc IEEE EMBS, 2012, pp. 2444 – 2447.

[4] T.T. Do et al., “Early melanoma diagnosis with mobile imaging,” in IEEE EMBC, 2014, pp. 6752–6757.




