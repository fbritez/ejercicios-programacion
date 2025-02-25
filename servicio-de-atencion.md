## Servicio de atencion medica
En un servicio de atención médica se desea implementar un sistema el cual permita a los recepcionistas cargar el ingreso de nuevos pacientes para ser atendidos y a los medicó poder ir llamándolos para poder resolver su consulta

Se nos pide entonces desarrollar un sistema el cual permita cargar la llegada de un nuevo paciente. De los pacientes conocemos su nombre, apellido y el plan de cobertura médica. Existen 3 tipos de planes de cobertura. básico, oro, premium.
Cuando el recepcionista atiende la llegada de un paciente realiza unas breves preguntas con el fin de identificar la gravedad de la consulta y la puede categorizar con niveles de gravedad, las cuales pueden ser baja, media o alta. Además el recepcionista registra hora de llegada del paciente.

Una vez ingresados en el sistema, los pacientes aguardan en sala de espera a ser atendidos. El médico entonces podrá consultarle al sistema cuál es el siguiente paciente.
El director médico del centro de atención decide dia a dia como se organizará la atención de pacientes por lo que el sistema deberá poder funcionar de la siguiente manera.
* Orden de llegada: En este caso, los pacientes serán atendidos en orden de llegada, es decir el que primero llega, primero es atendido. 
* Orden de gravedad: Los pacientes serán atendidos dependiendo del nivel de gravedad asignado por los recepcionistas, de tal modo, cada vez que el medio llame a un nuevo paciente, el sistema deberá evaluar sobre todos los pacientes y seleccionará al que tenga el nivel de prioridad más alto siendo alta  moderada  baja. Si hay dos pacientes con mismo nivel de gravedad se atenderá al haya llegado primero.
* Orden de cobertura & gravedad: Los pacientes serán atendidos dependiendo del nivel de cobertura que tengan y la gravedad asignada al momento de la recepción. Si hay un paciente con gravedad alta, tendrá prioridad, no importa el caso, pero luego se deberá atender al que tenga el nivel de cobertura mas alta, si hay mas de un paciente con mismo nivel de cobertura, se deberá atender al que tenga gravedad mas alta. Toma en cuenta, que esta forma de llamar a los pacientes podría dejar esperando a personas por mucho tiempo, por lo cual, es importante que si hay algún paciente con gravedad moderada o baja que haya estado esperando más de una hora, deberá de ser atendido antes de evaluar su cobertura.

Desarrollar un sistema que permita registrar ingresos y poder llamar a los pacientes para ser atendidos, el cual provea un protocolo que permita cambiar la forma de llamar a los pacientes.

El centro médico ahora desea implementar un sistema de pantallas para ser expuestas en la sala de espera. para ello nuestro sistema deberá interactuar con la interface ScreenReport con el fin de informar cada vez que un paciente el seleccionado.

```
public interface ScreenReport {
	
	public void report(String medicalPatientName);
	
}
```

Además los pacientes pueden tener instalada una aplicación en sus celulares las cuales les avisaron de un nuevo llamado de pacientes, con el fin de, según el caso, poder esperar en otro lugar del centro de atención evitando la sala de espera. 
Para ello nuestra aplicacion debera de interactuar con la interface PopUpMobile como la siguente

```
public interface PopUpMobile {
	
	public void push(String medicalPatientName);
	
}
```

Se pide implementar entonces la notificación necesaria para las pantallas y las aplicaciones móviles.




<details>
<summary>Soluciones esperadas</summary>

Strategy para las formas de llamar a los pacientes.
Observer & adpter para notificar quien ha sido llamado.

El sistema debera de tener al menos un mensaje que registre la llegada de un paciente y otro mensaje que devuelva un paciente segun la estrategia selecionada y saque a ese paciente de la lista
</details>
