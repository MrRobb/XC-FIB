# Routing Algorithms

Los routers se van preguntando entre ellos para tener información actualizada de sus enrutamientos.

> El objetivo es minimizar el número de saltos. Quiero que la ruta sea lo más rápido posible.

### Exterior (de frontera) vs Interior

Nosotros solo vamos a hablar de algoritmos interiores. Suponiendo que las subredes son iguales y que el criterio es único.

## [RIP](https://networkfaculty.com/es/video/detail/34-rip---introduccion): Routing Information Protocol

> Problema 2 del examen de 3/11/2016

#### RIP Update

Es un mensaje de actualización que se envía a todos los routers a los que está conectado.

##### ¿Cada cuanto?

Solamente envío cuando hayan cambios (por ejemplo, si cae un router). Pero claro, si se muere un router, no podré saberlo, necesito saber que los routers siguen activos. Por tanto, se marca un tiempo mínimo para actualizar la información. Cada **30 segundos** recibo una actualización.

##### Si hace 31 segundos que no me dice nada. ¿Qué hago? ¿Cuánto espero?

Si me precipito, podría hacer un cambio brusco de enrutamiento innecesario. Por lo tanto, se esperan **180 segundos**. Si no recibo nada en 180 segundos, decido que está muerto (RIP router).

##### ¿Qué información se envía?

En la tabla de enrutamiento, yo guardo: `el destino, el gateway, el interface y la métrica` (es el número de **saltos** que necesito para llegar a la máquina de destino).

La información que se envía es lo que el router sabe (un vector de distancias / saltos).
