### Split Horizon

> No devuelven la información que se le ha dado por el mismo interfaz.

### Poisoned Reverse

> Enviar un infinito para decir: "hey, no me envies nada de esta dirección por aquí."

El infinito se programa con un 16.

## Open Shortest Path First (OSPF)

En este algoritmo, se envía un mapa de todo lo que te me han contado. Voy más allá de sólo saltos, envío más información sobre mis alrededores.

- Se transmite sobre IP.
- Se distribuye usando `flooding`.
- Sólo se envían mensajes cuando ocurre algún cambio. A no ser que me pidas un update.
- Se usan dos protocolos:
	- Protocolo `hello`
	- Protocolo para enviar información de estado.
- Se envían muchas métricas (es más sofisticado).

## Classless Inter-Domain Routing (CIDR)

#### Conceptos

#### Classless

No tiene en cuenta las clases de las direcciones IP.

##### Agregar

Agregar entradas en la tabla de enrutamiento en tablas de routing

> Si yo tengo:

- 200.200.0.0 / 24	->	Rx
- 200.200.1.0 / 24	->	Rx

> Si las uno **(AGREGACIÓN)**, Podría hacer:

- 200.200.0.0 / 23	->	Rx

Y me ahorro una entrada / fila en la tabla de páginas.

##### Sumarizar

Sumarizar es agregar en la misma clase. Pero como estamos hablando de **classless** siempre hablaremos de agregación.
