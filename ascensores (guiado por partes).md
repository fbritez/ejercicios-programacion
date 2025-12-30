Ascensores

Dada la siguentes clases e infterfaces, diseñe y codifique una clase Ascensor que implemente la interface AscensorBehavior.
La implementacion y diseño son libres mientras que sean dentro del paradigamorientado a objetos. 

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
	 * Devuelve el numero de piso de la llamada mas cercana al piso actual
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
