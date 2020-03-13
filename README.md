# R-Graficas
Pequeño manual personal para poder crear y manipular gráficas en R.

En R, los tipos de acciones existentes para trabaja con gráficas se dividen en 3 grandes grupos:
* *Alto nivel*: Son funciones que crean nuevas gráficas, ejes, etiquetas, títulos, etc.
	* Gráfico de líneas
	* Gráfico de dispersión
	* Gráfico de puntos
	* Diagrama de cajas
	
* *Bajo nivel*: Son funciones que añaden nueva información a una gráfica ya existente, como puede ser una nueva línea, punto, etc.
* *Interactivas*: Son funciones que nos permiten interactuar con los gráficos haciendo uso de un apuntador, como puede ser un ratón.
Para realizar nuestra primera gráfica en R vamos a usar la función *plot* (la cual veremos en profundidad más adelante) y el conjunto de datos *pressure*. Este dataset muestra la presión del vapor de mercurio en función de su temperatura.

```r
> str(pressure)
'data.frame':    19 obs. of  2 variables:
 $ temperature: num  0 20 40 60 80 100 120 140 160 180 ...
 $ pressure   : num  0.0002 0.0012 0.006 0.03 0.09 0.27 0.75 1.85 4.2 8.8 

> plot(pressure$temperature, pressure$pressure)
> title("Temperatura vs Presion")
```

*GRÁFICO1*

## Función Plot

La función *plot* es una función genérica usada para la creación de gráficos. Esta función, creará un tipo de gráfico u otro dependiendo del tipo de argumento pasado por parámetro. Las diferentes opciones son:

* *plot(x, y)* . Siendo /x/ e /y/ dos vectores, esta acción crea un gráfico de dispersión de y sobre x.

```r
help("mtcars")
str(mtcars)
plot(mtcars$wt, mtcars$mpg)
```

*GRÁFICO2*

* *plot(x)*. Siendo /x/ una serie temporal, esta acción genera un gráfico de lineas temporal. 

```r
help("AirPassengers")
str(AirPassengers)
AirPassengers
plot(AirPassengers)
```

*GRÁFICO3*

* *plot(x)*. Si x es un vector formado por números complejos, esta función genera un gráfico de puntos de la parte imaginaria sobre la parte real de los elementos.

```r
a = 2i + 5
b = 3i + 6
c = 6i + 3
d = 4i + 3
e = 3.5i + 2
v = c(a,b,c,d,e)
plot(v)
```

*GRÁFICO4*

* *plot(f)*. Siendo /f/ un factor, genera un diagrama de barras de f.

```r
help("discoveries")
str(discoveries)
f = factor(discoveries)
plot(f)
```

*GRÁFICO5*

* *plot(f, y)*. Siendo /f/ un factor e /y/ un vector numérico, genera un diagrama de cajas de y para nivel de f.

```r
mtcars$cyl
cylfact = factor(mtcars$cyl)
cylfact
mtcars$mpg
plot(cylfact, mtcars$mpg)
```

*GRÁFICO6*

* *plot(df)*. Siendo df un data frame o hoja de datos, esta función genera gráficos de todas las parejas de variables del data frame.

```r
help(trees)
str(trees)
trees
plot(trees)
```

*GRÁFICO7*

* *plot(~ expr1 + expr2 + …)*. Siendo expr variables de un data frame, esta expresión genera parejas de gráficas, de manera similar a a la expresión anterior.

```r
plot(~mtcars$mpg + mtcars$cyl + mtcars$wt)
```

*GRÁFICO8*

## Otros tipos de Gráficas
Además de la función *plot*, existen otras maneras de generar gráficas en R. Veamos algunas funciones:

* *dotchart(x)*. Con esta función, podemos crear un gráfico de puntos de x.

```r
> precip
             Mobile              Juneau             Phoenix         Little Rock 
               67.0                54.7                 7.0                48.5 
        Los Angeles          Sacramento       San Francisco              Denver 
               14.0                17.2                20.7                13.0 
           Hartford          Wilmington          Washington        Jacksonville 
               43.4                40.2                38.9                54.5 
              Miami             Atlanta            Honolulu               Boise 
               59.8                48.3                22.9                11.5 
            Chicago              Peoria        Indianapolis          Des Moines 
               34.4                35.1                38.7                30.8 
            Wichita          Louisville         New Orleans            Portland 
               30.6                43.1                56.8                40.8 
          Baltimore              Boston             Detroit    Sault Ste. Marie 
               41.8                42.5                31.0                31.7 
             Duluth Minneapolis/St Paul             Jackson         Kansas City 
               30.2                25.9                49.2                37.0 
           St Louis         Great Falls               Omaha                Reno 
               35.9                15.0                30.2                 7.2 
            Concord       Atlantic City         Albuquerque              Albany 
               36.2                45.5                 7.8                33.4 
            Buffalo            New York           Charlotte             Raleigh 
               36.1                40.2                42.7                42.5 
            Bismark          Cincinnati           Cleveland            Columbus 
               16.2                39.0                35.0                37.0 
      Oklahoma City            Portland        Philadelphia           Pittsburg 
               31.4                37.6                39.9                36.2 
         Providence            Columbia         Sioux Falls             Memphis 
               42.8                46.4                24.7                49.1 
          Nashville              Dallas             El Paso             Houston 
               46.0                35.9                 7.8                48.2 
     Salt Lake City          Burlington             Norfolk            Richmond 
               15.2                32.5                44.7                42.6 
     Seattle Tacoma             Spokane          Charleston           Milwaukee 
               38.8                17.4                40.8                29.1 
           Cheyenne            San Juan 

> precip[1:10]
       Mobile        Juneau       Phoenix   Little Rock   Los Angeles    Sacramento 
         67.0          54.7           7.0          48.5          14.0          17.2 
San Francisco        Denver      Hartford    Wilmington 
         20.7          13.0          43.4          40.2 
> dotchart(precip[1:10])
```

*GRÁFICO9* 

* *barplot(x)*. Genera un gráfico de barrras donde x es una matriz o un vector.

```r
> carb = table(mtcars$carb)
> carb

 1  2  3  4  6  8 
 7 10  3 10  1  1 
> barplot(carb)
```

*GRÁFICO10*

* *pie(x)*. Genera un gráfico de tarta dónde x es un vector.

```r
> pr = precip[1:5]
> pr
     Mobile      Juneau     Phoenix Little Rock Los Angeles 
       67.0        54.7         7.0        48.5        14.0 
> pie(pr)
```

*GRÁFICO11*

* *pairs(x)*. Siendo x una matriz o una hoja de datos, esta función genera pares de gráficos entre sus variables.

```r
help("pressure")
str(pressure)
pairs(pressure)
```

*GRÁFICO12*

* *coplot(a ~ b | c)*. Siendo a y b vectores numéricos y c un vector numérico o un factor, esta función genera pares de gráficos de a sobre b para cada valor de c.

```r
coplot(mtcars$mpg ~ mtcars$wt | factor(mtcars$cyl))
```

*GRÁFICO13*

* *hist(x)*. Siendo x un vector numérico, esta función genera un histograma de la frecuencia de los valores de x. Esta función puede recibir varios parámetros como *nclass = n* para mostrar únicamente n clases, o *labels = TRUE* para mostrar el número de ocurrencias, o *breaks = v*, donde v será un vector que indica los cortes a tener en cuenta.

```r
hist(discoveries)
```

*GRÁFICO14*

## Funciones Gráficas de Bajo Nivel
las funciones gráficas de nivel bajo que son aquellas que modifican los gráficos, añadiendo texto, ejes, etiquetas, etc.

* *type = “x”*. La función type es un parámetro de la función plot, e indica el tipo de gráficos que queremos. Los valores son:
	* type=”p” Dibuja puntos individuales.
	* type=”l” Dibuja líneas.
	* type=”b” Dibuja puntos y líneas que los unen.
	* type=”o” Dibuja puntos y líneas que los unen, cubriéndolos.
	* type=”h” Dibuja líneas verticales desde cada punto al eje X
	* type=”s”,type=”S” Dibuja un gráfico de escalera. En la primera forma, la escalera comienza hacia la derecha, en la segunda, hacia arriba.

```r
> nilo = Nile[1:10]
> nilo
 [1] 1120 1160  963 1210 1160 1160  813 1230 1370 1140
> plot(nilo, type = "p")
> plot(nilo, type = "l")
```

*GRÁFICO15*
*GRÁFICO16*

* *type = “n”* y *text(x,y,t)*. Con type = “n”, pintaremos la estructura del gráficos pero sin puntos ni líneas. Luego, añadimos la función text(x,y,t) para escribir en las coordenadas x,y el valor t.

```r
> pr = precip[1:5]
> pr
     Mobile      Juneau     Phoenix Little Rock Los Angeles 
       67.0        54.7         7.0        48.5        14.0 
> plot(pr, type = "n")
> text(c(1:5), pr, names(pr))
```

*GRÁFICO17*

* * *main(x)* y *sub(x)*.La función main establecerá un título para el gráfico, mientras que la función sub establece un subtitulo. Ambas son argumentos de las funciones de alto nivel.
* *title(main, sub)*. Esta función tiene el mismo objetivo que los dos argumentos anteriores, solo que se usan como una función independiente.
* *axis(side, x)*. También podemos configurar los valores de los ejes. Para ello usaremos la función axis, donde side puede tener los valores 1 (abajo), 2(izq), 3(arriba), 4(derecha). Para usar esta función, debemos establecer en la función plot el argumento /axes = FALSE/

```r
> plot(pr, type = "p", axes = FALSE, main = "Precipitaciones por ciudades", sub = "Conjunto de datos filtrado", xlab = "Ciudades", ylab = "Cantidad")
> axis(1, 1:5, names(a))
> axis(2, c(10,20,30,40,50,60,70))
```

*GRÁFICO18*

* * *legend(x,y,text)*. También podemos crear una leyenda. A la hora de crear la leyenda tendremos en cuenta dónde queremos situarla (valores x e y), que texto queremos que aparezca y si deseamos algunos colores.

A continuación vamos a crear un gráfico combinado de 2 conjuntos de datos y estableceremos su leyenda.

```r
plot(ldeaths, type = "l", col = "blue", ylim = c(500, 5000))
lines(mdeaths, col = "red")

legend(1978, 4500, legend = c("ldeaths", "mdeaths"), col = c("blue", "red"), lty = 1:1)
```

*GRÁFICO19*

### Otros elementos gráficos

* *pch = x*. Indica el tipo de punto con él queremos el gráfico. Valor por defecto a 1.
* *lty = x*. Indica el tipo de línea.
* *lwd = x*. Indica el ancho de la línea.
* *col = x*. Indica el color de la línea o punto.  [Tabla de colores](https://www.statmethods.net/advgraphs/parameters.html) 
* *font = x*. Es un número que indica el tipo de fuente en el texto. 1 = Normal, 2 = Negrita, 3 = Itálica, 4 = Itálica negrita

```r
> # Tipo de punto
> plot(mtcars$mpg, pch = 6)
> plot(mtcars$mpg, pch = 5)
> # Tipo de linea
> plot(mtcars$mpg, type = "l", lty = 4)
> plot(mtcars$mpg, type = "l", lty = 2)
> # Ancho de linea
> plot(mtcars$mpg, type = "l", lty = 2, lwd = 2)
> plot(mtcars$mpg, type = "l", lty = 2, lwd = 3)
> # Color
> plot(mtcars$mpg, type = "l", lty = 2, lwd = 3, col = 2)
> plot(mtcars$mpg, type = "l", lty = 2, lwd = 3, col = 3)
> # Tipo de fuente
> plot(pr, type = "n")
> text(c(1:5), pr, names(pr), font = 2)
> plot(pr, type = "n")
> text(c(1:5), pr, names(pr), font = 3)
```

### Ejemplos

1. Gráfico de barras que represente la cantidad de vehículos que hay para los distintos valores de la variable /mtcars$cyl/:
	* Establece un color para cada una de las barras.
	* Añade al gráfico un título y un subtitulo.

```r
> mtcars$cyl
> unique(mtcars$cyl)

> tcyl = table(mtcars$cyl)

> barplot(tcyl, col = c("blue", "orange", "grey"))
> title("Gráficos de Barras", "Número de coches que tienen n cilindros")
```

*GRÁFICO20*

2. Haciendo uso de los datasets /mdeaths/, /ldeaths/ y /fdeaths/, realiza un gráfico donde:
	* Los 3 conjuntos de datos deben quedar representados como un gráfico de líneas.
	* El eje y debe quedar limitado al máximo y el mínimo de los valores.
	* Las líneas de /mdeaths/ serán continuas mientras que la de /ldeaths/ y /fdeaths/ serán discontinuas.
	* Las líneas de /fdeaths/ deben ser más anchas que las otras dos.
	* Las tres líneas deben tener colores distintos, quedando claro cuál es cada una en una leyenda.
	* Por último, cambia el nombre a los ejes x e y.

```r
mdeaths
ldeaths
fdeaths
maximo = max(mdeaths, ldeaths, fdeaths)
minimo = min(mdeaths, ldeaths, fdeaths)

plot(mdeaths, col = "red", ylim = c(minimo - 100,maximo + 1000), xlab = "Año", ylab = "Nº muertes")
lines(ldeaths, col = "blue", lty = 2)
lines(fdeaths, col = "green", lty = 2, lwd = 3)
legend(1978, 5000, legend = c("mdeaths","ldeaths","fdeaths"), 
       col = c("red","blue","green"), lty = c(1,2,2), lwd = c(1,1,3))
```

*GRÁFICO21*

3. Haciendo uso del dataset /precip/:
	* Filtra el dataset quedándote únicamente con los primeros 5 valores.
	* Crea un gráfico donde aparezca el nombre de cada ciudad en lugar del valor.
	* Dibuja aquellos nombres cuyo valor sea menor a 20 de color rojo y en cursiva.
	* Dibuja aquellos nombres cuyo valor sea mayor a 20 de color azul y en negrita.

```r
pr = precip[1:5]
prmenor = pr[pr < 20]
prmayor = pr[pr >= 20]

plot(prmayor, type = "n", ylim = c(min(prmenor), max(prmayor)), xlim = c(1,sum(length(prmayor), length(prmenor))))
text(c(1:length(prmenor)), prmenor, names(prmenor), font = 3, col = "red")
text(c(length(prmenor)+1:length(prmayor)), prmayor, names(prmayor), font = 2, col = "blue")
```

*GRÁFICO22*

## Gráficos en 3D y Gráficos Interactivos
Para empezar, debemos comenzar instalando la librería desde RStudio en la pestaña /packages/. Una vez instalada, debemos importarla con la función *library*.

Existen numerosas librerías que nos permiten crear distintos tipos de gráficos, pero nos centraremos en una:  plotly.

*SS*

Ahora, vamos a ver distintos tipos de gráficos.

* *Gráfico de puntos.* Para ello, vamos a usar la función *plot_ly(df,x,y,z)*, donde debemos df es el conjunto de datos, y /x,y,z/ son los valores que queremos representar en cada eje.

```r
> library(plotly)
> plot_ly(mtcars, x = ~wt, y = ~hp, z = ~qsec) %>% add_markers()
```


*GRÁFICO23*

La función *add_markers()* añade los puntos al gráfico.
Además, podemos dividir los puntos en colores en función de otra variable del dataset.

```r
# Cambiamos la lista de 0 y 1 de mtcars$am por Automatico y Manual. 
mtcars$am[which(mtcars$am == 0)] <- 'Automatico'
mtcars$am[which(mtcars$am == 1)] <- 'Manual'w
mtcars$am <- as.factor(mtcars$am)

plot_ly(mtcars, x = ~wt, y = ~hp, z = ~qsec, color = ~am, colors = c("red","blue")) %>% add_markers()
```

*GRÁFICO24*

* *Gráfico de líneas.* Para el gráfico de líneas, usaremos la misma función pero concatenando la funcion add_lines().

```r
library(plotly)

# Cambiamos la lista de 0 y 1 de mtcars$am por Automatico y Manual. 
mtcars$am[which(mtcars$am == 0)] <- 'Automatic'
mtcars$am[which(mtcars$am == 1)] <- 'Manual'
mtcars$am <- as.factor(mtcars$am)

plot_ly(mtcars, x = ~wt, y = ~mpg, z = ~qsec, color = ~am, 
        colors = c("blue", "red")) %>% add_lines()

# Podemos añadir puntos y lineas       
plot_ly(mtcars, x = ~wt, y = ~mpg, z = ~qsec, color = ~am, 
        colors = c("blue", "red")) %>% add_lines() %>% add_markers()
```

*GRÁFICO25*

* *Gráfico de superficie*. Para este tipo de gráfico, volveremos a usar la función /plot_ly/ pero añadiremos la función add_surface(). Un buen dataset para ver este gráfico es /volcano/. Usaremos la función *add_surface()*

```r
plot_ly(z = volcano) %>% add_surface()
```

*GRÁFICO26*

* *Gráfico de barra.* De la misma forma, podemos crear gráficos de barras, concatenando la función *add_bars()*.

```r
plot_ly(mtcars, x = ~cyl, y = ~mpg, color = ~am, colors = c("blue", "red")) %>% add_bars()
```

*GRÁFICO27*

* *Mapa de calor.* Con la función *add_heatmap()* podemos obtener un mapa de calor.

```r
plot_ly(z = volcano) %>% add_heatmap()
```

*GRÁFICO28*

* *Histograma.* Podemos crear un histograma con la función *add_histogram()*.

```r
fact = factor(mtcars$cyl)
fact
plot_ly(mtcars, x = fact) %>% add_histogram()
```

* *Gráfico de tarta*. También se pueden crear gráficos de tarta añadiendo *add_pie()* a la función plot_ly.

```r
pr = precip[1:5]
ds = data.frame(
  labels = names(pr),
  values = pr
)
ds
plot_ly(ds, labels = ~labels, values = ~values) %>% add_pie()
```
