## Pila Perfecta

Se desea implementar dentro del paradigma de programación orientada a objetos un tipo abstracto de dato pila, el cual tendrá el siguiente protocolo

  * push. El cual recibirá una palabra como parámetro y será almacenada en la pila.
  * pop: El cual no recibe parámetros, y deberá de retornar el último elemento agregado. Si la pila está vacía, debería de retornar el string 'Esta pila esta vacia'

Ejemplo de uso 

```
private Pila pila = new Pila()

pila.push('Hola')
pila.push('Mundo')

String elemento = pila.pop()
# elemento tiene el valor 'Mundo'

String elemento2 = pila.pop()
# elemento2 tiene el valor 'Hola'

String vacio = pila.pop()
# vacio tiene el valor 'Esta pila esta vacia'

String vacio2 = pila.pop()
# vacio2 tiene el valor 'Esta pila esta vacia'

```

Desafio:
* Implementar la solución dentro del paradigma de programación orientada a objetos
* Implementar la solución sin usar instrucciones if/else ni try/catch ni ningun otro hack de lenguaje. El diseño planteado debe de por ser implementado en cualqueir lenguaje y funcionar.



Link util: https://en.wikipedia.org/wiki/Linked_list


<details>
<summary>Soluciones esperadas</summary>
Las restricciones del desafio están dadas para explotar el uso de objetos en el modelado de la solución.
No serán soluciones válidas la implementación de la pila con una lista y preguntando si está vacía o no o intentando sacar elementos y atrapando las excepciones en caso de lista vacía.

Patrones que se esperan utilizar: Null Patern



</details>
