# Sistema de apoyo a la decisión cínica para el estudio de lesiones de piel basado en aprendizaje automático

## Información

- **Universidad** : Universidad de Sevilla.
- **Centro de estudio** : Escuela Técnica Superior de Ingeniería Informática.
- **Título del proyecto** : Sistema de apoyo a la decisión cínica para el estudio de lesiones de piel basado en aprendizaje automático.
- **Palabras clave**: Redes neuronales convolucionales, Detección de lesiones de piel, Aprendizaje profundo, Segmentación semántica, Sistema de asistencia clínica
- **Tutor**: Isabel de los Ángeles Nepomuceno Chamorro.
---
- **Autor**: Antonio Jesús García Nieto.
- **Correo de contacto**: antgarnie1@alum.us.es
---

## Resumen del proyecto y objetivos.
En este proyecto se pretende realizar un estudio exploratorio de modelos basados en redes neuronales convolucionales aplicados a la detección temprana de lesiones de piel. Los objetivos de este proyecto se pueden resumir en:
 1. Crear un modelo compacto que permita realizar la clasificación y segmentación de imágenes de lesiones de piel con mayor precisión que un especialista médico. 
 2. Ser capaz de aportar una visión general del aprendizaje profundo.

## Mapa del repositorio 

|-- Código -> En esta carpeta se encuentran separado por experimento todos los cuadernillos y documentos referente a la investigación practica.

|-- Documentación -> Se encuentra la ultima versión del TFG y algunos resumenes de artículos que han sido de interes durante la evolución del proyecto.

|-- Img -> Se encuentran las imágenes del proyecto.

| -- README.md --> Readme del proyecto.
 
## Experimentos.
Es recomendable ejecutar los cuadernillos suministrados en este repositorio de forma remota en la plataforma de Google, Colaboratory. Para ello tan solo necesitamos:
1. Descagar el cuadernillo desde el repositorio.
2. Subirlos a https://colab.research.google.com/

¡Listo!, ya podemo ejecutar el cuadernillo sin necesidad de realizar ningúna instalación o dependencias.

**_Nota_** : *En caso de querer trabajar en local es necesario realizar la instalación de un número considerable de paquetes y módulos. Estos vienen recojidos en la sección herramientas dentro del documento del TFG*

## Demo.
### Enlaces.
Se puede probar el clasificador en la siguiente demo:
- https://mvp-tfg.herokuapp.com/

**_Nota_**: *Esta demo no es una app en versión estable. Es un extra que pretende aportar una idea de como se podría aplicar el conocimiento obtenido durante la investigación en un contexto realista.*

### Requisitos para el lanzamiento en local
Si quieres correr esta demo en local necesitaras tener instalado es necesario tener las siguientes dependencias instaladas.
 - requests
 - coverage
 - Django
 - Pillow
 - tensorflow-cpu== 2.4.1
 - numpy
 - matplotlib
 - opencv-python-headless

### Guía de uso.
La pagina de inicio de la demo consta de un menú de navegación compuesto por tres secciones: inicio, readme del proyecto y log in.

Para probar la demo completa debemos seguir el siguiente flujo:
 1. **Crear un usuario.** Para ello clickamos en log in, aquí y completamos el formulario.
 2. **Crear un dossier con una imágen.** Una vez loggeados nos aparecerá una nueva opción en la barra de navegación: "Listado de dossieres", clickamos en ella, posteriormente en el simbolo [+] y rellenamos los campos indicados: título del dossier, imágen y título de la imagen. Pinchamos en aceptar.
 3. **Analizar la imágen.** Clickamos de nuevo en "listado de dossieres". Nos aparecerá el nuevo dossier. Pinchamos en ver en detalles. Nos mostrará la información referente a la imágen. Damos a analizar y nos aparecerá un resultado semejante a esto:

![Screenshot_24](https://user-images.githubusercontent.com/45717153/121396595-d2bcf700-c953-11eb-9f4d-a6718261029a.png)


¡Listo! nuestra lesión ya ha sido clasificada por una CNN.

**_Nota:_** _Por motivos prudenciales la red clasificadora cargada tiene pesos aleatorios._


