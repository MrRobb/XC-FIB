## IP (dudas)

> Interface es un nivel de hardware, por ejemplo, Ethernet.

### Cómo funciona el enrutamiento

No se hace a mano (aunque se puede hacer a mano, se puede programar). Pero lo normal es que haya mecanismos automáticos (que veremos en el tema 3).

Las tablas se actualizarán según unos algoritmos que veremos más tarde.

### Fragmentación

El nivel de transporte, para conectarse con otro nivel de transporte envía una información TCP o un datagrama. Y poco a poco luego, le va enviando paquetes de información en protocolo IP.

Para enviar cada paquete IP tienes que poner una cabecera. En esta cabecera está escondida información.

Si yo pido un vídeo, el servidor no me va enviar el vídeo entero, sino que me va devolviendo el vídeo a trozos.

> La cuestión es ¿de qué tamaño deben ser estos paquetes?

Eso lo determina transporte. Y le pasa esa información a IP. Que a su vez se lo envía al "hardware".

Cada protocolo admite un tamaño máximo de datos. El MTU es quien marca el tamaño del paquete.

> Cada subred puede tener MTU's diferentes, por eso, no puedes guardar un identificador de orden ya que si el MTU es más pequeño, tenemos un problema. Ya que al REFRAGMENTAR ¿qué identificador de orden le metes a cada uno de los paquetes (que están entre los ya numerados)?

> MTU: Maximmum Transfer Unit (datos + todos los headers)

Normalmente el tamaño es entre 1000 y 2000 bytes. Por lo tanto, IP tiene que fragmentar la información para poder enviarla.

Lo bueno es que estos datos fragmentados se pueden enviar de manera independiente. Sin embargo, la fragmentación es algo que intentamos evitar (es complejo).

Estos trozos que van a viajar de manera independiente por posibles rutas diferentes se reconstruyen en cada subred en la que viaja. Así cuando llega a la máquina de destino ya está construido.

Para que no se mezclen, tengo que tener un identificador del datagrama original. Y luego hago los trozos. Que cuando me lleguen sabré que son del mismo origen.

#### Orden

> Si tengo 20 bytes de cabecera y 1000 de datos, y la siguiente red tiene un MTU de 420. Fragmentaría la información en 2 de 20 + 400 y otro de 20 + 200.

Cada trozo tiene un identificador de orden que marca el número de desplazamiento (offset) respecto al principio del paquete.

Este offset está almacenado en un campo de la cabecera.

Para no dejarse ningún fragmento de los que me lleguen (yo sé el orden pero no sé cuando termina) guardo el tamaño del paquete entero en la cabecera.

> bit DF: Don't Fragment
> bit MF: More Fragments

¿Cómo sé yo que han llegado todos los paquetes (los grandes)? Tengo un bit en la cabecera que indica si faltan más fragmentos (MF: 1) o he terminado (MF: 0). Para reducir el nombre de bits del número de bloques, numero en bloques de 8 bytes.
