# Tarea-3
## Punto 1
En este punto tenemos que encontrar las funciones de densidad marginal $X$ y de $Y$ pero para ello se aplicaron las siguientes ecuaciones, pero 
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

<img src="https://latex.codecogs.com/gif.latex?f(y)&space;=&space;\frac{1}{\sqrt{2\pi(6,027)^2}}&space;*&space;exp[\frac{-(x-15,08)^2}{2(6,027)^2}]" title="f(y) = \frac{1}{\sqrt{2\pi(6,027)^2}} * exp[\frac{-(x-15,08)^2}{2(6,027)^2}]" />


