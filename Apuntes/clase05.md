# Protocolos de red

### DHCP

> Siglas: Dynamic Host Configuration Protocol. Dinámico en este caso significa que es automático. Configuración es la configuración de host que necesita para interactuar en IP (dirección IP, nombre (asociado a un dominio DNS), gateway (router que te da acceso al exterior)).

> ¿Qué hace? Cuando arranco la máquina (normalmente), el servidor DHCP te da una configuración (dirección IP + nombre + gateway) para poder interactuar a través de IP.

- Dirección IP: es una dirección de subred.
- Máscara de la subred.
- Nombre: es un dominio de nombre que sigue una jerarquía.
- Gateway: te da acceso al exterior.
- Dirección del servidor DNS local.

> ¿Cómo lo hace? Yo lanzo un mensaje de broadcast preguntando por alguien que me pueda dar mi configuración y solamente el servidor DHCP me puede contestar.
>
> Cuando hago la pregunta, si hay más de dos servidores DHCP, cada uno lanza una propuesta y yo, el cliente, escojo la que quiera. Aunque normalmente solo tengo un servidor DHCP (normalmente el router). DHCP funciona sobre UDP, (no sobre IP, ni sobre transporte).
>
> Es sin conexión. Pero claro, ¿cómo hago yo el broadcast sin tener ni siquiera mi IP? Pongo todo a 1. Lo enviaré a la dirección de destino especial 255.255.255.255 y lo enviaré desde la dirección de origen 0.0.0.0. Todo esto en el discover.
>
> En el request, uso la dirección de destino que me ha venido en el offer.

> Notas: yo puedo tener más de un servidor DHCP.

#### Flujo de mensajes

**CLIENT <---> SERVIDOR**

1. DHCP discover --->

"Busco configuración. Escucho ofertas."

2. DHCP offer <---

"Aquí tienes mi oferta."

3. DHCP request --->

"Vale, acepto. Quiero esta oferta."

4. DHCP ack <---

"Aquí tienes tu configuración."

> También puede haber un No Ack que sería un "no te acepto".

### NAT

> Siglas: Network Address Translation. En realidad el NAT no es un protocolo, es un servicio.

> ¿Qué hace? El NAT resuelve el problema de traducir una dirección privada (dentro de una subred) a una dirección pública en el exterior de la subred.

> ¿Cómo lo hace? En el datagrama, el router intercambia la dirección de origen de privada (de la cabecera) y pone una dirección pública que tenga disponible (son de pago). Porque fuera de una subred yo no puedo tener una dirección privada, sólo públicas.

El router tiene una tabla en la que pone (ejemplo):

|Dirección privada|Dirección pública|
|-----------------|-----------------|
|10.0.10.3|200.200.0.100|

> Substituye la dirección privada por la pública y el receptor, cuando le llegue, devolverá el mensaje a la dirección pública. El router la recogerá y volverá a traducir la dirección (ahora pública) a la privada que tenía anteriormente. Y borrará la fila de la tabla.

##### NAPT / PAT

Network Address Port Translation
Port Address Translation

> Para aprovechar una dirección pública con varias direcciones privadas. Se usan... ports. Los ports de 0 a 1024 detectan el tipo de protocolo (o servicio que se quiere usar) el resto, los puedo usar para tener una sola dirección pública con varios ports, cada uno identificará a una sola dirección privada. El port está en la cabecera de transporte, no está en la cabecera de IP.

##### DNAT

Destination Network Address Translation

> El caso contrario, quiero dar varias direcciones públicas a una sola dirección privada.

### DNS

> Siglas: Domain Name System.

> ¿Qué hace? Es el protocolo según el cuál tú le das un nombre al servidor DNS y este te da una dirección IP.

> ¿Cómo lo hace? Antes de poder preguntar, tengo que tener una dirección DNS. Esta dirección te la da el servidor DHCP.
