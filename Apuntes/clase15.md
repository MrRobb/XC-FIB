```c
// En general
velocidad efectiva =  ventana / RTT
```

> En la cabecera, lo que viaja en el sequence number, no empieza en 0, empieza en un número aleatorio.

### MSS (Maximmum Segment Size)

> Es el tamaño máximo de payload (tamaño máximo de los trozos de información que envío).

### Window Scale Factor

> La potencia de 2 por la que se multiplica el Advertised Window.

```c
Advertised Window = 2 ^ (Window Scale Factor) * (Advertised Window)
```

> Nota: el Advertised Window es el máximo número de bytes que puedo enviar sin recibir un ACK anterior. La separación (en bytes) del último ACK y lo que voy a enviar (no puede sobrepasar ese máximo).

### Timestamp

> Es una marca de tiempo, normalmente de cuando sale el paquete (puede servir para medir el tiempo que tarda en volver el paquete).

### SACK

> En caso de error, indica los bloques de segmentos consecutivos correctos recibidos para selective ReTx (?).
