## Medium Access Control Address

> **Broadcast:** FF-FF-FF-FF-FF-FF

Modo promiscuo: lee todas las tramas que pasan por la red. El Sistema Operativo evita que puedas enviar una trama ethernet tal cual.

Hay más de un protocolo viajando por la red, no solo IP.

### Carrier Sense Multiple Access

> Se asigna un tiempo aleatorio a cada uno de los emisores (se esperan ese tiempo) y vuelven a enviar a ver si hay mejor suerte la próxima. --> es el más usado y el más eficiente.

### Multi-Access protocol

> Piden turnos. Hay un token que se va pasando de dispositivo en dispositivo, y le otorga la palabra.

### Carrier Sense Multiple Access / Collision Detection

```c
// ...
```

### Dividirse en canales

2.4GHz -> 3 channels

# Ethernet

- Carrier Sense: wait for link to be idle
- Collision Detection: listen while transmitting
- Random Access:

|Preamble|Dest. Address| Source Address | Type | Data | CRC |
|--------|-------------|----------------|------|------|-----|
|--------|-------------|----------------|------|------|-----|

## Switch

[SWITCH]-------[ROUTER]

||||||||||||||

PC PC PC

> Depende de la velocidad del chip del switch puede ser que pueda gestionar más de una conexión a máxima velocidad (velocidad física del cable).

> No hay dominio de Broadcast

## Full-duplex Ethernet
