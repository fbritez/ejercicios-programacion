# Smart Calendar

Se nos pide desarrollar un calendario inteligente para ser ejecutado en celulares, el cual le permitirá al usuario poder recibir notificaciones sobre sus eventos.
Nuestro calendario debe registrar eventos de dos tipos: cumpleaños y pagos.
De los cumpleaños conocemos la fecha de nacimiento y el nombre del contacto que cumple años. De los pagos, conocemos el servicio que debemos pagar, la fecha de vencimiento exacta del pago y el monto.
Diariamente nuestro calendario evaluará todos los eventos  y notificará al celular de los eventos mediante un PhonePopUpInterface. 

Solo serán notificados los eventos según la siguiente lógica:
*  Cumpleaños. Solo el dia del cumpleaños exacto.Se enviara mensaje “No te olvides de saludar a NOMBRE_DEL_CONTACTO por su cumpleaños número AÑOS”. 
*  Pagos: 5 dias antes del vencimiento de la servicio, se enviará diariamente el mensaje “No te olvides de pagar NOMBRE_DEL_SERVICIO son MONTO_A_PAGAR pesos. El pago vence en DIAS_FALTANTES_PARA_EL_VENCIMIENTO dias”. una vez pasada la fecha, no se enviaran notificaciones. 

Este calendario le permitirá al usuario recibir diferentes tipos de alertas mediante la interfaz, la cual luce de la siguiente manera:

```
public interface PhonePopUpInterface {
	
	public void pushNotification(String message, Integer mode);
	/*
	 *  String message: mensaje que va a ser enviado a travez del celualr
	 *  Integer mode :  1 - Notificaciones por mail, para el mail registrado en el telefono.
	 *  				2 - Notificaciones para la barra de notificaciones
	 *  				3 - Notificaciones via popup del telefono 
	 */
}
```
Entonces es necesario que el usuario pueda elegir entre recibir la alerta mediante un popup en la pantalla del celular, un email o una notificación, o una combinación de las anteriores (es decir un usuario puede elegir recibir un email y una notificación y otro usuario puede preferir una notificación y un popup en el celular). Para ello  es importante interactuar de la manera que describe la interface y el calendario debe de poder mantener el registro seleccionado al momento de evaluar los eventos.


Se pide diseñar una solución la cual permita implementar lo descrito anteriormente.
Es importante mantener registro de los los eventos, inclusive los que hayan pasado.


### Solución
<details>
<summary>Soluciones esperadas</summary>
Strategy para poder seleccionar los modos email, popup o notificación e interactuar con la interfaz de modo tal de poder invocarla con los parámetros necesarios.
Composite para poder seleccionar más de un modo. 
Polimorfismo para tratar de igual manera a los pagos y los cumpleaños. 
</details>


## Smart Calendar + Eventos públicos.

Se nos pide incorporar en nuestro calendario el registro de eventos público, los cuales responden el siguiente protocolo:
```
public interface PublicEvent {
	
	public LocalDate eventDate();
	public String description()
}
```

Los eventos deberán de poder ser registrados de igual manera que se registran los cumpleaños y los pagos y deberán enviar notificaciones solo cuando la fecha del dia sea exactamente la fecha del evento.

### Solución
<details>
<summary>Soluciones esperadas</summary>
Adapter para adaptar el modelo actual a la interface
</details>



## Smart Calendar + Notificaciones inteligentes

Se nos pide poder anticiparnos con más (o menos) tiempo a los eventos del calendario, por lo cual cada evento podrá definir cuantos días antes comenzará a enviar las notificaciones.
De modo tal, podría existir un cumpleaños que determinados días antes, comience mandar notificaciones con el siguiente mensaje “Faltan DIAS_PARA_EL_EVENTO días para el cumpleaños de NOMBRE_DE_CONtACTO”. 
De la misma manera, se respetar el comportamiento para los pagos, pero la cantidad de dias para avisar con antelacion podra ser configurada por el usuario, manteniendo 5 dias como comportamiento por defecto.

Para tener notificaciones más inteligentes y personalizadas, se nos pide poder definir formas de notificaciones específicas para cada uno de los eventos. Es decir, además de la selección del calendario, el usuario podra indicar que para ciertos eventos, la notificación sea diferente. Por ejemplo: Un calendario envia emails para notificar todos los eventos salvo para el pago de la cuenta de luz, de la cual recibirá una notificación, un mail y un popup en su celular.

Se pide entonces poder configurar cada evento de calendario de modo tal de poder recibir notificaciones diferencias (del mismo tipo que los modos de notificación que ya conocemos) para eventos particulares. Para los eventos que no tiene una configuración específica, se enviará la notificación seleccionada en el calendario.

### Solución
<details>
<summary>Soluciones esperadas</summary>
Strategy en la jerarquía de eventos.
NullPattern para los eventos sin selección. null como variable es una mala decisión.
</details>

