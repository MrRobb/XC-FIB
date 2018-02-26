## Direcciones IP

**¿Cuántos bits usaremos para codificar las direcciones IP?**

Antes eran 32 bits (versión 4), luego 128 (versión 6)

[8 bits].[8 bits].[8 bits].[8 bits]

|0..255|0..255|0..255|0..255|
|-|-|-|-|

##### La dirección 10.1.1.0/24
- **10.1.1.0 Es la dirección de red + dirección de host**
- **24** son los bits (de los 32 que tiene) que **indican la dirección de la red** y los **8 restantes** (hasta 32) son los que **indican la dirección del host**.

#### Máscara de red

Para indicar máscara de subred en vez de poner (/24) también se puede expresar con una dirección, tal que en este caso sería **255.255.255.0** ya que si haces una `&` bit a bit entre `10.1.1.0 & 255.255.255.0` --> independendientemente de lo que hubiese en los 8 bits del final, siempre se seleccionarían los 24 primeros.

#### Dirección de red

La dirección de host con todo ceros no se puede usar, ya que es equivalente a la de red. En nuestro caso 10.1.1.0 sería la dirección de red y no se puede usar como host. 10.1.1.56 SÍ. 10.1.1.0 NO.

#### Dirección de broadcast

Tampoco se puede usar la dirección de broadcast. Que sería con todo 1's. En nuestro caso 10.1.1.255. 10.1.1.47 SÍ. 10.1.1.255 NO.


#### Dirección del router

Tampoco se puede usar la dirección de router. Que dependiendo de la red será diferente.

#### Calcular número máximo de hosts

Sabiendo los bits de máscara de subred y quitandole las direcciones de red, broadcast y router, puedo calcular el número máximo de hosts posibles que puede haber en la red.

#### Routers

Los routers siempre tienen 2 o más direcciones IP. Ya que conectan siempre 2 o más redes. Tendrán una dirección IP por red.

### Direccionamiento

#### Direccionamiento público

Me permite acceder desde cualquier lugar. Es una dirección **única** mundialmente.

Las direcciones públicas son de pago.

#### Direccionamiento privado

Está en un rango prefijado y conocido por todo el mundo. Estas direcciones sí que **pueden estar repetidas**. Aunque haya más máquinas que direcciones, como hay repetidas, puede funcionar.

Sin embargo, una máquina no puede navegar por el mundo con una dirección privada. Por lo tanto, en el momento que quieras salir más allá de internet, tendrás que mapear (con un servicio de soporte) esa dirección privada a una pública.

Las direcciones privadas son "gratis".

#### Rangos de direcciones privadas comunes

10.0.0.0 - 10.255.255.255

172.16.0.0 - 172.32.255.255

192.168.0.0 - 192.168.255.255

#### Clases de direcciones

Inicialmente las direcciones se organizan en clases:

|0|X|X|X|X|X|...|
|-|-|-|-|-|-|---|

- **CLASE A:** 8 bits para red, 24 bits para hosts
	- En realidad son 7 de red ya que siempre empiezan por 0 (para identificar que son de clase A).

|1|0|X|X|X|X|...|
|-|-|-|-|-|-|---|

- **CLASE B:** 16 bits para red, 16 bits para hosts
	- En realidad serían 14 bits de red ya que siempre empiezan por 1 y 0 (para identificar que son de clase B).

|1|1|0|X|X|X|...|
|-|-|-|-|-|-|---|
- **CLASE C:** 24 bits para red, 8 bits para hosts
	- En realidad serían 21 ya que siempre empiezan por 1, luego 1 y 0 (para identificar que son de clase C).

Hoy en día los números de bits de red y los números de bits son variables ya que internamente se racionan.

#### Ejemplo: Capacidad máxima con un rango 220.10.0.0/25

```
2 ^ (32 - 25) - 2 - Routers
```
