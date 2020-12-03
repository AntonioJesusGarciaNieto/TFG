# Herramientas.

En esta sección se detalla cuáles han sido las herramientas y librería usadas durante el TFG y porque han sido elegidas.

### Lenguaje de programación.

El lenguaje utilizado es python. Se decidió usar este lenguaje por el gran soporte que tiene por parte de la comunidad y en especial por la gran cantidad de librerías que tiene a su disposición. Se utilizará en su versión 3. La cual elegiremos por su compatibilidad con Colab y por ser más legible y actual que la versión 2. 

### Entorno.

El entorno utilizado es Colab. Colab es un servicio web basado en los cuadernos Jupyter. Algunos de sus principales beneficios son :
- Permite usar GPUs y TPUs de forma gratuita.
- Permite mantener activa la sesión durante un mínimo de 12 h en su versión gratuita.
- Por defecto posee instaladas numerosas librerías listas para importar y usar.

### Librerías

- Numpy - Es la librería matemática estándar.
- Pandas - Es una extensión de la librería Numpy, permite la manipulación y el análisis de datos. Se usó para generar el marco de datos,hacer un estudio del set de datos y posteriormente balancearlo.
- Seaborn - Es una librería que permite realizar gráficas de alto nivel de forma más atractiva que otras librerías similares como Pylab o Matplotlib.
- Tensorflow -Es una librería de código abierto dedicada al aprendizaje automático. Fue creada por Google, lo cual implica compatibilidad con colab y además cuenta con una amplia comunidad.
- OpenCV - Es una librería libre de visión artificial originalmente desarrollada por Intel. OpenCV significa Open Computer Vision. La usaremos para leer y redimensionar imágenes, será especialmente útil durante la fase de análisis de datos.
- Scikit-learn - es una librería para aprendizaje automático de software libre. Será usada como complemento a Tensorflow para realizar algunas tareas de forma más intuitiva.