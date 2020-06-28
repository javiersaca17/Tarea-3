# Tarea-3 MPSS (B66418)
## Punto 1
En este punto tenemos que encontrar las funciones de densidad marginal X y de Y pero para ello se aplicaron las siguientes ecuaciones, pero 
primero definimos lo que seria la función marginal de X: 

<a href="https://www.codecogs.com/eqnedit.php?latex=f(x)&space;=&space;\int_{-\infty}^{&plus;\infty}&space;f_{x,y}(x,y)&space;\cdot&space;dy&space;=&space;\frac{d}{dx}F_{x}(x)" target="_blank"><img src="https://latex.codecogs.com/svg.latex?f(x)&space;=&space;\int_{-\infty}^{&plus;\infty}&space;f_{x,y}(x,y)&space;\cdot&space;dy&space;=&space;\frac{d}{dx}F_{x}(x)" title="f(x) = \int_{-\infty}^{+\infty} f_{x,y}(x,y) \cdot dy = \frac{d}{dx}F_{x}(x)" /></a> 

Tambien la otra contraparte que es la función marginal de Y: 

<a href="https://www.codecogs.com/eqnedit.php?latex=f(y)&space;=&space;\int_{-\infty}^{&plus;\infty}&space;f_{x,y}(x,y)&space;\cdot&space;dx&space;=&space;\frac{d}{dy}F_{y}(y)" target="_blank"><img src="https://latex.codecogs.com/svg.latex?f(y)&space;=&space;\int_{-\infty}^{&plus;\infty}&space;f_{x,y}(x,y)&space;\cdot&space;dx&space;=&space;\frac{d}{dy}F_{y}(y)" title="f(y) = \int_{-\infty}^{+\infty} f_{x,y}(x,y) \cdot dx = \frac{d}{dy}F_{y}(y)" /></a>

Debido a que se esta en presencia de variables dscretas como es el caso de la marginalidad de esta variables X, Y las funciones marginales son las probabilidad de hallar X y tambien Y. Usamos la función de numpy trabajando con la matriz que proviene del archivo xy.csv. Ya que se calcula la pdf pero a nivel marginal se busca un modelo de mejor ajuste dependiendo de las condiciones que tiene cada variable, dentro de las opciones el mejor ajuste es de la distribución normal y lo mejor es que se ajusta tanto para la pdf de X, como para la pdf de Y por lo cual ese fue el factor determinante para elegir ese tipo de distribución, para encontrar dichos valores se hizo uso del método de curve_fit, los,parametros que se encontraron para cada variable se presentan a continuación:

|Variable pdf|<img src="https://latex.codecogs.com/gif.latex?\mu" title="\sigma" />|<img src="https://latex.codecogs.com/gif.latex?\sigma" title="\mu" />|
|---|---|---|
|Y|6.028|15.10|
|X|2.28|9.91|

Construyendo los repectivos modelos tenemos el siguiente modelo para X:

<img src="https://latex.codecogs.com/gif.latex?f(x)&space;=&space;\frac{1}{\sqrt{2\pi(2.28)^2}}&space;*&space;exp[\frac{-(x-9.91)^2}{2(2.28)^2}]" title="f(x) = \frac{1}{\sqrt{2\pi(2.28)^2}} * exp[\frac{-(x-9.91)^2}{2(2.28)^2}]" />

El modelo respectivo para Y con los valores de los parametros evaluados:

<img src="https://latex.codecogs.com/gif.latex?f(y)&space;=&space;\frac{1}{\sqrt{2\pi(6.028)^2}}&space;*&space;exp[\frac{-(x-15.10)^2}{2(6.028)^2}]" title="f(y) = \frac{1}{\sqrt{2\pi(6.028)^2}} * exp[\frac{-(x-15.10)^2}{2(6.028)^2}]" />

## Punto 2
Desde el supuesto que se asume independencia entre las variables se pueden multiplicar las dos variables por separado, con lo cual la función de densidad conjunta conjunta se puede encontrar más facil asumiendo dicha proposición:

<img src="https://latex.codecogs.com/gif.latex?f(x,y)&space;=&space;f(x)&space;*&space;f(y)&space;=&space;\frac{1}{\sqrt{2\pi(2.28)^2}}&space;*&space;exp[\frac{-(x-9.91)^2}{2(2.28)^2}]&space;*&space;\frac{1}{\sqrt{2\pi(6.028)^2}}&space;*&space;exp[\frac{-(x-15.10)^2}{2(6.028)^2}]" title="f(x,y) = f(x) * f(y) = \frac{1}{\sqrt{2\pi(2.28)^2}} * exp[\frac{-(x-9.9)^2}{2(2.28)^2}] * \frac{1}{\sqrt{2\pi(6.028)^2}} * exp[\frac{-(x-15.10)^2}{2(6.028)^2}]" />

## Punto 3
## Calculo de la correlación
Para el cálculo de la correlación entres nuestras variables marginales X, Y, sabiendo que la correlación es una de tantas técnicas estadisticas que es usada para determinar la relación entre las variables, sabiendo que la correlación puede ser al menos de dos variables o de una variable dependiente y dos o más variables independientes que en ese caso estamos en la presencia de una correlación múltiple. En nuestro caso especifico como se trata de una variable discreta con lo cual se hace una sumatoria de la multiplicación de cada término de X con cada término de Y, usando la siguiente fórmula:

<img src="https://latex.codecogs.com/gif.latex?R_{xy}&space;=&space;\int_{-\infty}^{&plus;\infty}\int_{-\infty}^{&plus;\infty}xyf_{x,y}(x,y)&space;\cdot&space;dx&space;dy" title="R_{xy} = \int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}xyf_{x,y}(x,y) \cdot dx dy" />


Con un for fue que se recorrio toda la matrzi de probabilidades que estaba contenida en el archivo "xyp.csv" , el resultado que se obtivo de haber realizador dicho for es el siguiente: 

<img src="https://latex.codecogs.com/gif.latex?\inline&space;R_{xy}&space;=&space;149.59" title="R_{xy} = 149.59" />

Con lo cual con un valor alto de 149.59 podemos asegurar que existe una alta correlación entre ambas variables.

## Calculo de la Covarianza
La covarianza es el valor que refleja en que cuantía dos variables aleatorias varían de forma conjunta respecto a sus medias, la covarianza se calcula se calcula de manera parecida que la correlación en este caso hay que tener cuidado restarle a las variables el valor de la media ya que estamos en el caso de una distribución nominal que es con el siguiente parámetro  <img src="https://latex.codecogs.com/gif.latex?\mu" title="\mu" />. Usamos la siguiente ecuación para el calculo de la covarianza:

<img src="https://latex.codecogs.com/gif.latex?C_{xy}&space;=&space;\int_{-\infty}^{&plus;\infty}\int_{-\infty}^{&plus;\infty}(x-\bar{X})(y-\bar{Y})f_{x,y}(x,y)&space;\cdot&space;dx&space;dy" title="C_{xy} = \int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}(x-\bar{X})(y-\bar{Y})f_{x,y}(x,y) \cdot dx dy" />

El resultado es el siguiente: <img src="https://latex.codecogs.com/gif.latex?C_{xy}&space;=&space;0.06669" title="C_{xy} = 0.06697" />, con lo cual vemos que es un valor positivo (mayor a cero), con lo cual como mencionamos anteriormente podemos afirmar que la correlación es de tipo directa, este concepto se explica de mejor manera en el coeficiente de Pearson pero en el caso especifico de la covarianza es que a grandes valores de Y corresponden grandes valores de X y al reves también, eso explica la relación directa en covarianza.



## Coefiente de Pearson
El coeficiente de correlación es un valor cuantitativo de la relación entre dos o más variables. El coeficiente de correlación puede variar desde -1.00 a 1.00, la correlación de proporcionalidad directa o positiva se establece con los valores +1.00 y de proporcionalidad inversa o negativa -1.00, si no existe relación entre la variables cuando el coeficiente es de 0.00. Para calcular el coeficiente de Pearson es necesario antes calcular la covarianza que ya lo hicimos en el punto anterior, de dicho caso se necesita saber cual es la variación estandar  de las respectivas variables X, Y teniendo una distribución normal corresponde al siguiente parámetro <img src="https://latex.codecogs.com/gif.latex?\sigma" title="\sigma" />, con lo cual con ayuda de este parametro que es para ambas variables X, Y con lo cual calculamos el respectivo coeficiente de correlación de Pearson: 

<img src="https://latex.codecogs.com/gif.latex?\rho&space;=&space;\frac{C_{xy}}{\sigma_x&space;\sigma_y}" title="\rho = \frac{C_{xy}}{\sigma_x \sigma_y}" />

Evaluando en la función el Coeficiente de Pearson nos da que es de 0.003896 con lo cual podemos afirmar que la correlación entre las variables X, Y pues no es tan fuerte o alta como suponiamos dado que este valor es muy cercano a cero ya que esta en el equilibrio de una proporciionalidad directa e inversa. 

# Punto 4 
Las  gráficas de las funciones de densidad marginales de las variables X, Y reales se muestran a continuación: 

Para xFx:

![](https://github.com/javiersaca17/Tarea-3/blob/master/xfx_pdf%20real.png)

ParayFy:

![](https://github.com/javiersaca17/Tarea-3/blob/master/yfy_pdf%20real.png)





