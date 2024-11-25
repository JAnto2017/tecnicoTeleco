# Ejercicios IPv6

---

## Ejercicio 1: Identificar el tipo de dirección

Para cada una de las siguientes direcciones IPv6, identifica:

1. El tipo (Unicast Global, Link-Local, Multicast, etc.).
2. Si es enrutable o no.
3. Si es una dirección especial, indica su propósito.

Direcciones:

- [ ] 2001:0db8:1234:5678:9abc:def0:1234:5678
- [ ] fe80::1
- [ ] ff02::2
- [ ] ::1
- [ ] 2001:db8::abcd
- [ ] ::
- [ ] ::ffff:192.0.2.1

---

## Ejercicio 2: Simplificar direcciones IPv6

Simplifica las siguientes direcciones IPv6 siguiendo las reglas de eliminación de ceros iniciales y el uso de :: donde sea posible.

Direcciones:

- [ ] 2001:0db8:0000:0000:0000:0000:0000:0001
- [ ] fe80:0000:0000:0000:0202:b3ff:fe1e:8329
- [ ] ff02:0000:0000:0000:0000:0000:0000:0001
- [ ] 2001:0db8:0000:0000:0000:ff00:0042:8329

---

## Ejercicio 3: Expandir direcciones IPv6

Expande las siguientes direcciones IPv6 a su forma completa, incluyendo todos los ceros necesarios.

Direcciones:

- [ ] 2001:db8::1
- [ ] fe80::
- [ ] ff02::1
- [ ] ::ffff:192.0.2.128

---

## Ejercicio 4: Determinar si una dirección es válida

Indica si las siguientes direcciones IPv6 son válidas o inválidas, y explica por qué.

Direcciones:

- [ ] 2001:db8:1234:5678::abcd::1234
- [ ] fe80:0:0:0:0:0:0:1
- [ ] ::192.168.1.1
- [ ] 2001:db8::xyz
- [ ] ff03:0:0:0:0:0:0:1

---

## Ejercicio 5: Identificar el prefijo

Para cada una de las siguientes direcciones IPv6, identifica su prefijo y determina si pertenece a un rango específico:

Direcciones:

- [ ] 2001:4860:4860::8888
- [ ] fe80::abcd:1234:5678
- [ ] ff02::1:ff00:abcd
- [ ] 2001:0db8:abcd::1

---

## Ejercicio 6: Clasificar por tipo de tráfico

Indica si las siguientes direcciones IPv6 se usan para tráfico unicast, multicast, anycast o no tienen un uso estándar.

Direcciones:

- [ ] ff02::1
- [ ] ::1
- [ ] 2001:db8:abcd:1234::1
- [ ] ff05::2

---

## Ejercicio 7: Configurar una red

Dado el prefijo de red IPv6 2001:db8:abcd::/64, responde las siguientes preguntas:

- [ ] ¿Cuántas direcciones únicas están disponibles dentro de este rango?
- [ ] Proporciona 5 direcciones IPv6 válidas dentro de este rango.
- [ ] ¿Qué ventajas tiene dividir este prefijo en subredes más pequeñas, como /68 o /72?

---

## Ejercicio 8: Traducción de IPv4 a IPv6

Dada la dirección IPv4 192.168.1.1, escribe cómo se vería como una dirección IPv6 mapeada y convertida.

Respuesta esperada:

- [ ] IPv4 mapeada en IPv6.
- [ ] IPv4 embebida en IPv6.

---

## Ejercicio 9: Interpretar encabezados IPv6

Analiza los siguientes encabezados IPv6 (simplificados) e identifica:

1. La dirección de origen y destino.
2. El tipo de tráfico (si es unicast, multicast, etc.)

Ejemplo:
Encabezado:

- [ ] Versión: 6
- [ ] Dirección de origen: fe80::1
- [ ] Dirección de destino: ff02::1
