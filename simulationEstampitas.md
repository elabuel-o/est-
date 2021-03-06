Estampitas del Mundial, Neutrones y Casinos
========================================================

### Neutrones
En ciertas situaciones resulta buena idea hacer "experimentos" previos (muchas veces haciendo c�lculos mentales e imaginando escenarios hipot�ticos) para tener idea de un proceso cuyas caracter�sticas principales, *a priori*, desconocemos. 

Esto fue precisamente lo que se le ocurri� a Stanislaw Ulam en 1946, f�sico que entonces trabajaba en el Laboratorio Nacional de Los Alamos, en Estados Unidos (aqu�l en el que se desarroll� la bomba at�mica). Su trabajo consist�a, m�s o menos, en averiguar las caracter�sticas del proceso f�sico mediante el cual los neutrones atraviesan diversos metales. 

A pesar de que Ulam contaba con los datos necesarios para investigar este fen�meno, le resultaba pr�cticamente imposible resolver el problema con los m�todos convencionales, tales como la resoluci�n de ecuaciones matem�ticas; por tanto, a Ulam se le ocurri� atacar el problema mediante experimentos *aleatorios*.

Mientras estaba enfermo durante 1946, Ulam jugaba solitario (el juego de cartas) y se le ocurri� preguntarse cu�l ser�a la probabilidad de ganar un tipo de juego de solitario jugando con una baraja de 52 cartas; pronto se dio cuenta que era pr�cticamente imposible hacer el c�lculo a la manera tradicional (con f�rmulas de conteo y c�lculos de probabilidad), por lo que ide� una manera m�s f�cil: imaginar que se juega el juego muchas veces, quiz� cien o doscientas, y simplemente observar el n�mero esperado de juegos ganados. 

Este m�todo, de alguna u otra manera, lo quiso aplicar al problema de los neutrones y lo platic� con su colega John von Neumann (s�, el mismo von Neumann de la teor�a de juegos y un largo etc�tera), a quien le pareci� buena idea; entonces, decidieron aplicarlo. Pero como el objeto de las investigaciones en el Laboratorio de Los Alamos era secreto, von Neumann sugiri� ponerle al m�todo reci�n inventado un nombre clave: m�todo Monte Carlo, ya que lo relacion� con el famoso casino de M�naco (despu�s de todo, el m�todo se le ocurri� a Ulam jugando cartas).

A estas alturas alg�n lector se deber� estar preguntando qu� demonios tiene que ver esto con las estampitas que cada a�o de mundial de f�tbol la empresa Panini saca a la venta. Ahora lo veremos (si es que no se han aburrido).

### Estampitas
Cada cuatro a�os, Panini vende el �lbum del mundial de f�tbol, que hay que llenar con estampitas de los jugadores, los logos de las asociaciones de f�tbol, las fotos de los estadios, etc. Para el mundial de 2014 hay que llenar 640 estampitas, que se venden en sobrecitos de 5 estampitas: por lo tanto, hay que comprar, al menos, 128 sobrecitos para llenar un �lbum.

Es aqu� donde empiezan a surgir dificultades: uno pensar�a que es sumamente improbable que comprando 128 sobrecitos se pueda llenar un �lbum, ya que implicar�a no sacar ninguna estampita repetida. De ah� que, una primera pregunta que podemos hacernos es, �cu�l es la probabilidad de comprar, digamos, 600 sobrecitos y llenar un �lbum completo? Para obtener una respuesta, utilizaremos el m�todo Monte Carlo ideado por Ulam y von Neumann.

Imaginemos que le pedimos a 1,000 personas (seleccionadas de manera aleatoria) que compren 600 sobrecitos cada una (es decir 3,000 estampitas) y al final observamos los casos en los que una persona obtuvo un �lbum completo; podemos hacer esto *simulando* este experimento mental en la computadora y entonces calcular la probabilidad que nos interesa con una funci�n hecha en el entorno estad�stico R  (los c�digos para hacer el an�lisis se encuentran al fin del texto):





```
## monte.carlo
##   Completo Incompleto 
##      0.002      0.998
```


Vemos que, una vez hecha la simulaci�n en la computadora, la probabilidad de completar un �lbum es de 0.002. Esto concuerda con nuestra conjetura previa de que la probabilidad de llenar un �lbum comprando pocos sobrecitos es muy peque�a.

Por tal motivo, un coleccionista no querr� llenar el �lbum comprando �nicamente sobrecitos, sobre todo tomando en cuenta que cada sobrecito se vende a 6 pesos (si compra, como en el experimento, 600 sobrecitos, habr� gastado 3,600 pesos, �y a�n as� tendr� una probabilidad muy baja de llenar el �lbum!). Afortunadamente, existe un mercado "secundario" de estampitas *solas* o "repetidas", por lo que el coleccionista podr�a comprar, digamos 128 sobrecitos y comprar las estampitas faltantes para llenar el �lbum en dicho mercado. 

Ahora la pregunta es: �existe un n�mero de estampitas compradas (en sobrecito y solas) tal que minimice el costo de llenar un �lbum? Para responder esta pregunta, una vez m�s podemos hacer uso del m�todo Monte Carlo y del entorno R.

Supondremos que cada sobre con 5 estampitas tiene un precio de 6 pesos (1.2 pesos por estampita) y que cada estampita sola tiene un precio de 5 pesos. Simularemos la compra de un n�mero fijo de sobrecitos y asumimos que las estampitas que nos faltan para llenar el �lbum las adquirimos en el mercado alternativo. Por lo tanto, el costo de llenar el �lbum ser� $C = (n_1*p_1) + (n_2*p_2)$, donde $p_1$ y $p_2$ son los precios de las estampitas de sobrecito y solas, respectivamente, y $n_1$ y $n_2$ el n�mero de estampitas de sobrecito y estampitas solas compradas.

Esta funci�n nos ayudar� a entender el tipo de relaci�n que existe entre el costo *esperado* de llenar el �lbum y el n�mero de estampitas que debemos comprar. De existir, ser� f�cil conocer el n�mero de estampitas que debemos comprar (tanto en sobrecitos como solas) tal que llenar el �lbum nos cueste lo menos posible.







![plot of chunk graph](figure/graph.png) 


Hechas las simulaciones, vemos en la gr�fica que existe un n�mero de estampitas compradas tal que minimizamos el costo de llenar el �lbum del mundial: si compramos alrededor de 890 estampitas (las primeras 640 no repetidas de sobrecitos y las restantes en el mercado secundario) llenaremos el �lbum con alrededor de 1,850 pesos. Si por el contrario, decidimos adoptar una estrategia de comprar 1,500 estampitas, el costo de llenar el �lbum podr�a elevarse a m�s de 2,100 pesos. 

Como vemos, las ideas originales de Ulam y von Neuman nos ayudan a simular escenarios que de otra forma ser�a impr�ctico tratar, a�n si se trata de un tema tan divertido y aparentemente sencillo como el de las estampitas del �lbum Panini. Despu�s de todo, los m�todos de la f�sica (comportamiento de part�culas subat�micas como los neutrones) y la econom�a (problema dual de minimizaci�n de costos dado cierto nivel de "utilidad") no est�n tan alejados ;-) . 

### C�digo R utilizado

Ustedes pueden replicar los resultados y modificar los supuestos, como el precio de las estampitas y el n�mero m�nimo de estampitas a comprar, utilizando los c�digos de R que se muestran a continuaci�n:


```r
## Funci�n para muestreo de n estampitas a partir de m estampitas.
album.comp <- function(n, m) {
    estampitas <- sample(1:n, size = m, replace = TRUE)
    ifelse(length(unique(estampitas)) == n, "Completo", "Incompleto")
}
```



```r
## Simulaci�n para calcular la probabildad de comprar n estampitas y llenar
## un �lbum Simulamos con la funci�n album.comp y n = 640 (estampitas en el
## �lbum Panini) y m = 3000 (estampitas compradas, o sea 600 sobrecitos)
set.seed(4)  ## Para reproducibilidad
monte.carlo <- replicate(1000, album.comp(640, 3000))
table(monte.carlo)/1000  ## Probabilidad de llenar un �lbum con 3000 estampitas
```



```r
## Funci�n de costos La estampita de sobrecito vale 1.2 pesos (6 pesos / 5
## estampitas) La estampita del mercado secundario vale 5 pesos.  El costo
## ser� (costo1*estampita de sobre) + (costo2*estampita sola)
costos <- function(num, costo.sobre, costo.sola) {
    costo.sobre <- 1.2
    costo.sola <- 5
    muestra <- sample(1:640, size = num, replace = TRUE)
    n.comp <- length(unique(muestra))
    n.rep <- 640 - n.comp
    (num * costo.sobre) + (n.rep * costo.sola)
}
```



```r
## Generamos la gr�fica: Usamos sapply para almacenar el costo esperado en un
## vector:
sec <- 500:1500  ## secuencia de 700 a 1500 estampitas compradas
opt.cost <- sapply(sec, media.esp)
datos.graf <- data.frame(sec, opt.cost)

## Gr�fica:
library(ggplot2)

ggplot(datos.graf, aes(x = sec, y = opt.cost)) + geom_point(size = 2, colour = "blue") + 
    theme_grey() + theme(plot.title = element_text(size = rel(1.2)), axis.title.x = element_text(size = rel(1.2)), 
    axis.title.y = element_text(size = rel(1.2)), axis.text.x = element_text(size = rel(1.2)), 
    axis.text.y = element_text(size = rel(1.2)), legend.text = element_text(size = rel(1.2)), 
    legend.title = element_text(size = rel(1.2))) + labs(x = "Estampitas compradas", 
    y = "Costo esperado en pesos") + ggtitle("Costo esperado de estampitas (precios $1.2 y $5)")
```

