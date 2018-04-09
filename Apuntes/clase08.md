## Seguridad

Los servicios pueden ser:
- Preventivos
-
-

#### Mecanismos en nivel de IP

- Firewalls

> Reciben un datagrama y deciden si puede pasar o no puede pasar. Normalmente se implementa en el router. Los campos de la cabecera IP nos sirven como filtro.

> 20/01/2016 Problema 1 Apartado F

> 03/11/2016 Problema 1 (creo) Apartado F

- VPN (Virtual Private Networks)

> Si yo tengo dos subredes que no están juntas, pero yo quiero que estén juntas conectadas. Al estar lejos, es complicado unirlas físicamente. Por lo tanto, para hacer que pueda ver la subred que está superlejos, uso un **VPN tunnel** para poder mandarlo directamente por allí.

> ¿Cómo lo hago? Escondo mi datagrama dentro de otro datagrama (como si fuera un camión). Incluso en el datagrama interior yo puedo poner una dirección privada.
