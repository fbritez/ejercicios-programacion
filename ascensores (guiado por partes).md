# Ascensores

## Operaciones basicas
Dada la siguentes clases e interfaces, diseñe y codifique una clase Ascensor que implemente la interface AscensorBehavior.
La implementacion y diseño son libres mientras que sean dentro del paradigamorientado a objetos. No nos preocuparemos por la eficiencia ni la performance de los algoritmos, nos enfocaremos en el diseño.

<details>
<summary>Clases/Interfaces</summary>
 
```
public enum Direccion {
    SUBIR,
    BAJAR
}
```

```
public class Llamada {
    private Integer piso;
    private Direccion direccion;

    // Constructor
    public Llamada(Integer piso, Direccion direccion) {
        this.piso = piso;
        this.direccion = direccion;
    }

    // Getter para piso
    public Integer getPiso() {
        return piso;
    }

    // Getter para direccion
    public Direccion getDireccion() {
        return direccion;
    }
}
```

```
public interface AscensorBehavior {
	
	public Integer pisoActual();
	/*
	 * Devuelve el piso actual del ascensor 
	 */

	public void registrarLllamada(Llamada unaLlamada);
	/*
	 * Registra una llamada de un piso determinado
	 */

	public Integer proximoPiso(Llamada unaLlamada);
	/*
	 * Devuelve el numero de piso de la llamada mas cercana al piso actual.
	 * Ejemplos: Ascensor en el piso 3 con llamadas al piso 7, 5  y 9. El proximo piso es el 5.
	 *			 Ascensor en el piso 7 con llamadas al piso 9, 6  y 0. El proximo piso es el 6.
	 */

	public vodi setPisoActual(LInteger numeroDePiso);
	/*
	 * Setea el piso actual. Si el numeroDePiso es igual al proximoPiso, la llamada a ese piso desaparece.
	 */

  public Boolean estaEnMovimiento();
	/*
	 * Devuelve False si no tiene mas llamadas pendientes.
	 */
}
```
</details>

Nota: Un ascensor nuevo, inicia en el piso cero.

## Direcciones

Mejoremos la implementacion anterior. Para optimizar recorridos, el proximoPiso debera devolver el numero de piso de la llamada mas cercana, dependiendo si el ascensor esta subiendo o bajando. Para esto es necesario poder determinar si el ascensor esta subiendo o bajando, dependiendo de las llamadas que se registren y dependiendo de si el ascensor esta en movimiento o esta quieto. 

**Ejemplos ascensor quieto:**
*  Ascensor en el piso 3 **que no esta en moviiento**, recibe una llamada del piso 5. El ascensor esta  **subiendo** y el proximo piso es el 5.
*  Ascensor en el piso 3 **que no esta en moviiento**, recibe una llamada del piso 1. El ascensor esta  **bajando** y el proximo piso es el 1.
  
**Ejemplos ascensor en movimiento:**
*  Ascensor en el piso 3 **subiendo** con llamadas al piso 7, 5  y 9. El proximo piso es el 5.
*  Ascensor en el piso 3 **subiendo** con llamadas al piso 7, 2  y 9. El proximo piso es el 7.
*  Ascensor en el piso 3 **bajando** con llamadas al piso 7, 2  y 9. El proximo piso es el 2.
*  _Ascensor en el piso 3 **bajando** con llamadas al piso 7, 5  y 9. El proximo piso es el 5._

modifique interface AscensorBehavior con los siguientes mensajes:
```
public interface AscensorBehavior {
	 ... 
	public Boolean estaSubiendo();
	/*
	 * Devuelve true si el ascensor esta subiendo
	 */
}
```

## Palier
Para seguir mejorando los recorridos de un ascensor se nos pide implementar un Palier. El Palier controlar varios ascensores a la vez. El Palier recibe las llamadas y las distribuye entre los ascensores dependiendo el piso actual de cada uno, si estan en movimiento, si estan subiendo o bajando, de manera tal de poder atender de una manera mas optima las llamadas de los diferentes pisos.
Se pide ahora, diseñar e implementar una clase Palier que dentro de su protocolo tenga un mensaje que reciba una llamada y la distribuya entre los ascensores, priorizando a los ascensores que esten mas cerca de ese piso solicitado y la direccion en la que se esten moviendo. 

**Ejemplos basicos:**
*  Ascensor A en el piso 5 **que no esta en moviiento** y ascensor B en el piso 8 **subiendo** con proxima parada en el piso 10, recibe una llamada del piso 15. La llamada sera aginada al ascensor B.
*  Ascensor A en el piso 5 **que no esta en moviiento** y ascensor B en el piso 8 **subiendo** con proxima parada en el piso 10, recibe una llamada del piso 7. La llamada sera aginada al ascensor B.
*  Ascensor A en el piso 5 **que no esta en moviiento** y ascensor B en el piso 8 **subiendo** con proxima parada en el piso 10, recibe una llamada del piso 6. La llamada sera aginada al ascensor A.
*  Ascensor A en el piso 5 **que no esta en moviiento** y ascensor B en el piso 8 **bajando** con proxima parada en el piso 6, recibe una llamada del piso 9. La llamada sera aginada al ascensor B.
*  Ascensor A en el piso 5 **que no esta en moviiento** y ascensor B en el piso 8 **bajando** con proxima parada en el piso 2, recibe una llamada del piso 9. La llamada sera aginada al ascensor A.
*  Ascensor A en el piso 5 **que no esta en moviiento** y ascensor B en el piso 8 **bajando** con proxima parada en el piso 2, recibe una llamada del piso 4. La llamada sera aginada al ascensor A.
*  Ascensor A en el piso 5 **que no esta en moviiento** y ascensor B en el piso 8 **bajando** con proxima parada en el piso 2, recibe una llamada del piso 1. La llamada sera aginada al ascensor B.

**Notar:**
* Utilize los ejemplos como casos de unit tests para reforzar el uso de TDD y garantizar que su modelo cumple lo requerido.
* Extienda los casos de ejemplos basicos para casos donde los dos ascensores estan detenidos o los dos ascensores estan en movimiento.
* Extienda su diseño para que el Palier organice **n** ascensores recibiendo llamadas.
  
