# Sistema de Gestión de Catastro Provincial

La **Dirección de Catastro** de una provincia solicita el diseño de un sistema para medir las dimensiones de las ciudades que la componen y así aplicar correctamente el cobro de impuestos.

## Cálculo de Dimensiones
La unidad más pequeña que gestiona la Dirección de Catastro son las viviendas. Además, la provincia gestiona locales comerciales y edificios públicos. Para todos los casos, se deben registrar los metros cuadrados totales.

Por su parte, un conjunto de viviendas, comercios y edificios publicos se organizan en ciudades. Una ciudad grande puede organizarse internamente con ciudades mas pequeñas, como es el caso de Quilmes, que esta organizada en ciudades mas pequeñas como Bernal, Don Bosco, Ezpeleta, etc.

El sistema necesita entonces poder conocer la dimension total de una ciudad, para eso el sistema sumara las dimensiones de las unidades que compongan a la ciudad, mas un valor fijo (500-quinientos) por cada 10 unidades que directas que la ciudad contenga. Es decir una ciduad como Quilmes,  compuesta por seis ciudades mas pequeñas ( Quilmes, Bernal, Don Bosco, Ezpeleta, San Francisco Solano y Villa La Florida), solo sumara las dimensiones de cada una de las ciudades, tanto que la Ciudad de Buenos Aires compuesta por 48 ciudades, debera calcular la dimension de cada una de sus ciudades mas 2000 (4x500).  

---

## Política Impositiva
El cálculo de impuestos varía según el tipo de unidad.

Los edificios publicos no pagan impuestos.

Los comercios pagaran de a cuerdo a la declaracion de ganancias que hayan declarado en el ultimo mes. Si la ganancia declarada es igual a cero, no pagan impuestos. Si la ganancia declarada es mayor a cero pero menor a 5 millones, pagan un canon fijo de 1000 + un 10 por cada metro cuadrado de su dimension. Si la ganancia declarada es mayor a 5 millones durante el ultimo mes, el monto a pagar es 25 por cada metro cuadrado de dimension que posea. Cabe aclarar que los comercios declaran sus ingresos una vez por mes y que el calculo de los impuesto puede darse en cualquier momento. Un comercio durante un buen mes puede tener ganancias por mas de 5 millones un mes y al mes siguiente cero. Los comercios nuevos que no hayan declarado ganancias aun, seran considerados como ganancia cero.

El cobro para las viviendas, el monto dependerá del tipo de construcción que haya en ellas. Por el momento el municipio identificó 3 tipos de construcciones:
* Sin construcción: En ese caso, el valor del impuesto es un canon fijo de 1000.
* Propiedad horizontal (edificio o departamentos): De la cual se conocen la cantidad de departamentos de esa vivienda y el monto del impuesto se calcula como 10 por la cantidad de departamentos, multiplicado por las dimensiones de la vivienda - un 20% del total. Ejemplo: una vivienda de 70m2 que tiene 14 departamentos, pagará (10x14x70)x0.8 = 7840.
* Propiedades parquizadas: Son propiedades que tienen construcción parcial del terreno (como podría ser una casa con jardín). De las cuales se conoce cuántos metros cuadrados están construidos y cuántos sin construir. El monto a pagar para este tipo de vivienda es 3 por la cantidad de metros cuadrados sin construir + 8 por los metros construidos. Ejemplo: una casa con 90 m2 donde 50 son sin construcción, pagará: 50x3 + 40x8 = 470.

Importante: Una vivienda puede cambiar de tipo de construcción durante su vida, es decir, hoy puede ser una propiedad parquizada, mañana una propiedad horizontal y luego de una demolición una propiedad sin construcción, por lo que nuestro sistema tiene que poder contemplar estos casos. Una vivienda nunca podrá ser un comercio ni un edificio público.

Por último, para saber el monto que debe recaudar la dirección de catastro por una ciudad es la sumatoria de las unidades que la componen.


### Solución
<details>
<summary>Soluciones esperadas</summary>
Composite, donde ciudad es el compuesto y las viviendas, comercios y edificios publicos son las hojas.
  
Strategy, donde Vivienda es el contexto y las estrategias son las los tipos de construccion.

State, donde comercio es el cliente y los rangos segun las ganancias declaradas son los estados concretos.

Notar: La IA que me ayudo a formatear este archivo detecto que la relacion entre viviendas y tipo de vivienda se implementaba con un patro State. Que opinas al respecto? Discutir con la catedra
</details>
