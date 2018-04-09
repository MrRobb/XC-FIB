## UDP (User Datagram Protocol)

> UDP añade una cabecera.

Aplicación --> UDP (quien añade una cabecera) --> IP

Lo que añade en la cabecera es:
- Source Port: dirección de puerto de origen (16 bits)
- Destination Port: dirección de puerto de destino (16 bits)
- Length (16 bits)
- Checksum: de la cabecera y también parte del cuerpo y también parte de la dirección IP (16 bits)

> De puerto significa simplemente una dirección de transporte (que identifica una dirección de aplicación).

> TO-DO: complementar con las transparencias pero tampoco hace falta entrar en más detalle.

> Usaré cuando IP no pueda fallar --> IP nunca falla cuando solo actúo en mi red.

> Si envío un archivo grande no me sirve UDP (porque no controla errores).

## ARQ (Automatic Repeat reQuest)

Automaticamente se repite la transmisión si no se recibe una confirmación de recibido (ACK).

- **Tiempo de proceso**: son los tiempos de CPU. (son despreciables, por lo tanto tiende a 0)
- **Tiempo de propagación (tp)**: depende del medio y la distancia. (más o menos, la velocidad de la luz, si hay muy poca distancia, puede llegar a ser despreciable)
- **Tiempo de transmisión de datos (tt)**: depende de la cantidad de datos.
- **Tiempo de transmisión de ACKs (ta)**: normalmente es menor que el tiempo de transmisión de datos. Tiene la misma velocidad que la velocidad de transimisión de datos.
- **Tiempo de espera (tout)**: temporizador, es calculado por el software. RTO (Retransmission TimeOut)

> RTT (Round Trip Time): Es el tiempo que tarda en transmitir + recibir + ACK + recibir ACK.

## Protocolos

### Stop & Wait (S & W)

Envío paquete, espero ACK. Recibo el ACK.
Envío paquete, espero ACK, si no me llega, retransmito paquete.

### Transferencia continua

No me espero a que me llegue el ACK.

##### Go back N

Descarta desordenados.

##### Retransmisión selectiva

Toca reordenar.

## TCP (Transmission Control Protocol)

> Los ACKs son acumulados (significa "han llegado todos los anteriores") (se descartan duplicados).

> + transparencias página 9 (go back n / selective retransmission) hasta la página 14 (eficiencia con errores)
