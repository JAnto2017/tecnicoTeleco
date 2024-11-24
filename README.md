# Técnico Telecomunicaciones CCNA 200-301

- [Técnico Telecomunicaciones CCNA 200-301](#técnico-telecomunicaciones-ccna-200-301)
  - [Introducción](#introducción)
    - [Elementos de una red](#elementos-de-una-red)
    - [Símbología en las redes de datos](#símbología-en-las-redes-de-datos)
  - [Direccionamiento IP](#direccionamiento-ip)
    - [Máscara de subred](#máscara-de-subred)
    - [Clasificación de las direcciones IPv4](#clasificación-de-las-direcciones-ipv4)
      - [Clase A](#clase-a)
      - [Clase B](#clase-b)
      - [Clase C](#clase-c)
      - [Clase D](#clase-d)
      - [Clase E](#clase-e)
    - [Direcciones IPv4 especiales](#direcciones-ipv4-especiales)
      - [¿Por qué estas direcciones son de propósito privado?](#por-qué-estas-direcciones-son-de-propósito-privado)
      - [¿Se pueden asignar estas direcciones a los hosts?](#se-pueden-asignar-estas-direcciones-a-los-hosts)
      - [¿Por qué no se pueden usar en Internet?](#por-qué-no-se-pueden-usar-en-internet)
      - [Ventajas de usar redes privadas](#ventajas-de-usar-redes-privadas)
      - [Ejemplo práctico](#ejemplo-práctico)
    - [¿Qué es CIDR?](#qué-es-cidr)
      - [¿Cómo funciona el CIDR para subredes?](#cómo-funciona-el-cidr-para-subredes)
      - [Ventajas del CIDR](#ventajas-del-cidr)
      - [Ejemplo 1: Crear subredes de una red principal](#ejemplo-1-crear-subredes-de-una-red-principal)
      - [Ejemplo 2: Identificar la subred de una IP](#ejemplo-2-identificar-la-subred-de-una-ip)
  - [Protocolos TCP/IP](#protocolos-tcpip)
    - [Red LAN](#red-lan)
    - [Red WAN](#red-wan)
      - [Internet (WWW)](#internet-www)
    - [TCP/IP](#tcpip)

## Introducción

Técnico Telecomunicaciones CCNA es un curso con documentación sobre las configuraciones en las redes siguiendo la nomenclatura establecida en CCNA 200-301.

### Elementos de una red

Los principales elementos que componen las redes:

- Dispositivos finales: _Host_, _Servidores_.
- Dispositivos intermedios: _Router_, _Switch_, _Firewall_, _Access Points_.
- Medios físicos: _cables estructurados_ (cobre), _cables de fibra óptica_.
- Medios de transmisión inalámbricos: usan radiofrecuencia (WiFi), enlaces a través de satélites (WLAN)
- Tarjetas de red (NIC).
- Mapa del cableado mundial: [Cable submarino](https://www.submarinecablemap.com/).

### Símbología en las redes de datos

```mermaid
mindmap
    id)Simbología(
```

![alt text](image.png)

## Direccionamiento IP

Una dirección IPv4 es una línea de 32 bits, separados en cuatro grupos con 8 bits cada uno llamados _octetos_. Cada uno de los _octetos_ están separados entre sí por un punto.

Una dirección IPv4 está dividida en dos partes: una porción de bits direccionan la red y el resto de bits están destinados a direccionar los host.

- Las direcciones IPv4 que terminen en **0**, están destinadas a direccionar la **Red**.
- Los direcciones IPv4 que terminen en **255**, están destinadas al **Broadcas**.

### Máscara de subred

Representación de cuatro _octetos_ con 8 bits. Se ponen a 1 lógico todos los bits de la dirección IP destinados a direccionar la red, y el resto de bits se ponen a 0 lógico, son los destinados a direccionar los host.

```mermaid
mindmap
    id(Máscara = IP red + IP host)
```

### Clasificación de las direcciones IPv4

Dependiendo del rango, se determinan a qué clase pertenecen las direcciones IPv4.

| Clase | IP mínimo | IP máximo | Máscara (defecto) | Dir. Red | Dir. Host |
| :---: | --- | --- | :---: | ---: | :--- |
| A | 00000000.0.0.0 = 0.0.0.0       | 127.255.255.255 | R.H.H.H = /8 | 255. | .0.0.0 |
| B | **1**0000000.0.0.0 = 128.0.0.0 | 191.255.255.255 | R.R.H.H = /16 | 255.255. | 0.0 |
| C | **11**000000.0.0.0 = 192.0.0.0 | 223.255.255.255 | R.R.R.H = /24 | 255.255.255. | .0 |
| D | **111**00000.0.0.0 = 224.0.0.0 | 239.255.255.255 | multicast | - | - |
| E | **1111**0000.0.0.0 = 240.0.0.0 | 247.255.255.255 | investigación | - | - |

#### Clase A

- Propósito: Redes muy grandes, generalmente asignadas a grandes organizaciones o proveedores.
- Primer octeto (rango): 0 a 127 (en formato decimal).
- Rango total de direcciones:
  - Mínima: 0.0.0.0
  - Máxima: 127.255.255.255
- Bits iniciales: Siempre comienzan con 0.
- Rango de redes asignables:
  - Desde 1.0.0.0 (porque 0.0.0.0 es especial)
  - Hasta 126.255.255.255 (porque 127.x.x.x es reservado para loopback).
- Máscara predeterminada: 255.0.0.0 o /8
- Número de redes: 128 (aunque solo 126 asignables).
- Número de hosts por red: 2<sup>24</sup> − 2 = 16.777.214 (se excluyen la dirección de red y broadcast).

#### Clase B

- Propósito: Redes medianas, asignadas a universidades, empresas y organizaciones de tamaño medio.
- Primer octeto (rango): 128 a 191.
- Rango total de direcciones:
  - Mínima: 128.0.0.0
  - Máxima: 191.255.255.255
- Bits iniciales: Siempre comienzan con 10.
- Rango de redes asignables:
  - Desde 128.0.0.0
  - Hasta 191.255.0.0.
- Máscara predeterminada: 255.255.0.0 o /16
- Número de redes: 2<sup>14</sup> = 16.384.
- Número de hosts por red: 2<sup>16</sup> − 2 = 65.534.

#### Clase C

- Propósito: Redes pequeñas, utilizadas en organizaciones pequeñas o redes domésticas.
- Primer octeto (rango): 192 a 223.
- Rango total de direcciones:
  - Mínima: 192.0.0.0
  - Máxima: 223.255.255.255
- Bits iniciales: Siempre comienzan con 110.
- Rango de redes asignables:
  - Desde 192.0.0.0
  - Hasta 223.255.255.0.
- Máscara predeterminada: 255.255.255.0 o /24
- Número de redes: 2<sup>21</sup> = 2.097.152.
- Número de hosts por red: 2<sup>8</sup> − 2 = 254.

#### Clase D

- Propósito: Direcciones para multicast (comunicación a un grupo específico de dispositivos).
- Primer octeto (rango): 224 a 239.
- Rango total de direcciones:
  - Mínima: 224.0.0.0
  - Máxima: 239.255.255.255
- Bits iniciales: Siempre comienzan con 1110.
- Características:
  - No se dividen en redes y hosts.
  - No tienen máscara de subred.
  - Usadas en transmisión de datos como video o streaming.

#### Clase E

- Propósito: Reservadas para investigación y uso futuro.
- Primer octeto (rango): 240 a 255.
- Rango total de direcciones:
  - Mínima: 240.0.0.0
  - Máxima: 255.255.255.255
- Bits iniciales: Siempre comienzan con 1111.
- Características:
  - No se asignan a redes normales.
  - La dirección 255.255.255.255 es de **broadcast universal**.

Tabla resumen.

![alt text](image-3.png)

### Direcciones IPv4 especiales

1. **Dirección de red** (**0.0.0.0**)

   - _Propósito_: Representa una dirección "indeterminada". Se utiliza cuando un dispositivo no tiene aún una dirección IP asignada o para referirse a "todas las direcciones posibles".
   - _Ejemplo de uso_: Enrutadores que envían solicitudes para obtener una dirección IP por DHCP.

2. Dirección de **loopback** (**127.0.0.0/8**)

    - _Propósito_: Se usa para probar la comunicación dentro de un mismo dispositivo. Cuando envías datos a esta dirección, no salen de tu computadora.
    - _Rango completo_: Desde 127.0.0.0 hasta 127.255.255.255.
    - _Ejemplo de uso_: Probar si el protocolo TCP/IP funciona correctamente con ping 127.0.0.1. Esta dirección se conoce comúnmente como "localhost".

3. **Direcciones de red privada** (RFC 1918)

    - _Propósito_: Son direcciones reservadas para redes locales y no son enrutables en Internet.
    - _Rangos definidos_:
        - **10.0.0.0/8** (10.0.0.0 a 10.255.255.255)
        - **172.16.0.0/12** (172.16.0.0 a 172.31.255.255)
        - **192.168.0.0/16** (192.168.0.0 a 192.168.255.255)
    - _Ejemplo de uso_: Direcciones IP para redes domésticas o empresariales pequeñas.

4. Dirección de **broadcast** (**255.255.255.255**)

    - _Propósito_: Se usa para enviar datos a todos los dispositivos de una red local simultáneamente.
    - _Ejemplo de uso_: Mensajes ARP o descubrimiento de servicios en redes locales.

5. **Dirección de red limitada** (**169.254.0.0/16**)

    - _Propósito_: Direcciones asignadas automáticamente cuando un dispositivo no puede obtener una IP mediante DHCP.
    - _Rango completo_: Desde 169.254.0.0 hasta 169.254.255.255.
    - _Ejemplo de uso_: Un equipo desconectado de una red asignará una dirección dentro de este rango.

6. **Direcciones reservadas** para futuras investigaciones

    - _Propósito_: Estas direcciones están reservadas y no deben usarse en redes públicas ni privadas.
    - _Rangos conocidos_: **240.0.0.0/4** (240.0.0.0 a 255.255.255.254).

7. Dirección de red **multicast** (**224.0.0.0/4**)

    - _Propósito_: Se usa para enviar paquetes a un grupo específico de dispositivos en una red.
    - _Rango completo_: Desde 224.0.0.0 hasta 239.255.255.255.
    - _Ejemplo de uso_: Transmisión de datos de video o voz a múltiples receptores.

![alt text](image-1.png)

#### ¿Por qué estas direcciones son de propósito privado?

1. Reservadas por la IETF (**RFC 1918**):

   - Estas direcciones fueron definidas como privadas en el estándar RFC 1918, para evitar conflictos en Internet y garantizar que las redes internas puedan operar sin necesidad de direcciones públicas.
   - Esto significa que estos rangos **no son válidos en Internet**; no se pueden enrutar más allá de la red local (LAN).

2. Ahorro de direcciones públicas:

    - Las direcciones públicas (aquellas que pueden usarse en Internet) son limitadas. Al reservar estos rangos para uso interno, muchas organizaciones pueden reutilizarlos sin consumir direcciones públicas.
    - Por ejemplo: Dos empresas diferentes pueden usar 192.168.1.0/24 en sus redes privadas sin interferir entre sí.

3. Aislamiento de redes locales:

    - Estas direcciones permiten que los dispositivos de una red privada se comuniquen entre sí, pero necesitan un dispositivo como un router con **NAT** (Traducción de Direcciones de Red) para acceder a Internet.

Estos son los rangos específicos de redes privadas reservados:

![alt text](image-2.png)

#### ¿Se pueden asignar estas direcciones a los hosts?

¡Sí! Estas direcciones son perfectamente válidas para asignarlas a los hosts dentro de una red privada. Por ejemplo:

1. Asignación estática:

   - Puedes configurar manualmente una dirección como 192.168.1.10 en tu computadora si pertenece al rango de la red.
   - Asegúrate de incluir:
        - Dirección IP: Ej. 192.168.1.10.
        - Máscara de subred: Ej. 255.255.255.0 (para redes /24).
        - Puerta de enlace: Ej. 192.168.1.1 (el router).

2. Asignación dinámica (**DHCP**):

   - En redes modernas, un servidor **DHCP** (normalmente el router) asigna automáticamente direcciones privadas a los dispositivos.
   - Ejemplo: El router puede asignar direcciones del rango 192.168.0.2 a 192.168.0.254.

#### ¿Por qué no se pueden usar en Internet?

1. No enrutable en Internet:

    - Los routers de Internet están configurados para descartar paquetes provenientes de estas direcciones privadas. Esto evita que una red privada interfiera con otra en Internet.

2. NAT (Network Address Translation):

    - Para que un dispositivo con una IP privada acceda a Internet, necesita un router con NAT. Este traduce las direcciones privadas en una dirección pública válida que sí pueda enrutar.

#### Ventajas de usar redes privadas

1. Reutilización de direcciones:

    - Como estas direcciones no salen de la red local, diferentes redes privadas pueden usar los mismos rangos sin problemas.

2. Seguridad:

    - Las direcciones privadas están "ocultas" de Internet, lo que agrega una capa de protección frente a ataques externos.

3. Flexibilidad:

    - Puedes dividir estos rangos para múltiples subredes dentro de tu organización.

#### Ejemplo práctico

1. Red doméstica típica:

    - El router doméstico asigna direcciones del rango 192.168.1.0/24 a los dispositivos:
        - Computadora: 192.168.1.2
        - Teléfono: 192.168.1.3
        - Impresora: 192.168.1.4

2. Red empresarial:

    - Una empresa grande puede usar el rango 10.0.0.0/8 para configurar miles de subredes:
        - Subred para oficinas: 10.1.0.0/16
        - Subred para servidores: 10.2.0.0/16

En resumen:

- Estas direcciones son privadas porque están reservadas para redes locales y no son válidas en Internet.
- Sí se pueden asignar a hosts, pero solo dentro de una red privada.
- Para acceder a Internet desde estas redes, necesitas un router con NAT que traduzca las direcciones privadas en una pública.

### ¿Qué es CIDR?

El sistema de clases (Classful Addressing) ha sido reemplazado por el CIDR (Classless Inter-Domain Routing), que permite mayor flexibilidad al asignar redes de cualquier tamaño sin estar limitado a clases específicas.

El **CIDR** es un método de direccionamiento IP introducido para reemplazar el sistema rígido de clases de IPv4. Permite dividir redes en subredes de cualquier tamaño (de forma más eficiente) al usar máscaras de subred de longitud variable (VLSM).

- En vez de usar clases fijas (A, B, C), las direcciones IP con CIDR usan un prefijo para indicar cuántos bits son para la red.
- El prefijo CIDR se representa como /N, donde N es el número de bits en la máscara de red.

Por ejemplo: 192.168.1.0/24 indica que los primeros 24 bits son para identificar la red. Esto es equivalente a la máscara 255.255.255.0.

#### ¿Cómo funciona el CIDR para subredes?

Con CIDR, podemos crear subredes dividiendo una red principal en bloques más pequeños. Esto se hace aumentando el número de bits en la máscara de red.

Fórmulas clave para subredes:

1. Cantidad de subredes: 2<sup>𝑛</sup>, donde 𝑛 es el número de bits "prestados" de la parte de host para la parte de red.
2. Cantidad de hosts por subred: 2<sup>m</sup> − 2, donde m es el número de bits restantes para los hosts (se restan 2 para excluir la dirección de red y de broadcast).
3. Tamaño de cada subred: 2<sup>𝑚</sup>  direcciones (incluyendo red y broadcast).
4. Intervalo entre subredes: El incremento entre direcciones de red es igual al tamaño de la subred.

#### Ventajas del CIDR

1. Eficiencia: Permite asignar solo las direcciones necesarias sin desperdicio.
2. Flexibilidad: Las redes pueden ser del tamaño exacto que se requiere, sin ajustarse a las clases fijas.
3. Reducción de tablas de enrutamiento: CIDR puede agrupar múltiples redes en un solo prefijo, reduciendo la complejidad del enrutamiento (ej., agregación de rutas).

#### Ejemplo 1: Crear subredes de una red principal

Supongamos que tienes la red 192.168.1.0/24 y quieres dividirla en 4 subredes.

1. Determinar los bits necesarios para subredes:

   - 2<sup>𝑛</sup> ≥ 4, donde 𝑛 es el número de bits prestados.
     - 𝑛=2, porque 2<sup>2</sup> = 4.
   - Máscara original: /24 → Nueva máscara: /26 (se añaden 2 bits).

2. Tamaño de cada subred:

   - 2<sup>6</sup> = 64 direcciones por subred (32−26=6, bits para hosts).

3. Direcciones de red y broadcast: Dividimos en bloques de 64 direcciones:

   - Subred 1:
     - Dirección de red: 192.168.1.0
     - Dirección de broadcast: 192.168.1.63
     - Rango de hosts: 192.168.1.1 a 192.168.1.62
   - Subred 2:
     - Dirección de red: 192.168.1.64
     - Dirección de broadcast: 192.168.1.127
     - Rango de hosts: 192.168.1.65 a 192.168.1.126
   - Subred 3:
     - Dirección de red: 192.168.1.128
     - Dirección de broadcast: 192.168.1.191
     - Rango de hosts: 192.168.1.129 a 192.168.1.190
   - Subred 4:
     - Dirección de red: 192.168.1.192
     - Dirección de broadcast: 192.168.1.255
     - Rango de hosts: 192.168.1.193 a 192.168.1.254

#### Ejemplo 2: Identificar la subred de una IP

Supongamos que tienes la red 10.0.0.0/16 y te preguntan a qué subred pertenece la dirección 10.0.5.100 si divides en subredes de /20.

1. Tamaño de cada subred:

   - Máscara original: /16 → Nueva máscara: /20.
   - Número de bits para hosts: 32 − 20 = 12.
   - Tamaño de subred: 2<sup>12</sup> = 4.096 direcciones.

2. Intervalo entre subredes:

   - Cada subred abarca 4.096 direcciones.
   - Incremento entre subredes: 4,096 direcciones → En formato decimal, es un incremento de 16 en el tercer octeto (4.096/256=16).

3. Rangos de subredes:

   - Subred 1: 10.0.0.0 a 10.0.15.255
   - Subred 2: 10.0.16.0 a 10.0.31.255
   - Subred 3: 10.0.32.0 a 10.0.47.255 (y así sucesivamente).

4. Ubicación de la IP:

   - La dirección 10.0.5.100 pertenece a la primera subred, ya que está dentro del rango 10.0.0.0 a 10.0.15.255.

## Protocolos TCP/IP

### Red LAN

_Local Area Network_. Los dispositivos están en un área geográfica en común y están bajo una misma administración.

### Red WAN

_Wide Area Network_. Red amplia, por lo general son las redes de los proveedores de servicios. Permitiendo interconectar ciudades, países y continentes. Permiten interconectar con otros proveedores y con las redes LAN.

#### Internet (WWW)

Es la red _World Wide Web_. Es una red de redes interconectando resde WAN.

### TCP/IP

_Transport Control Protocol/Internet Protocol_. Permite la comunicación de manera estándar con los dispositivos en la red Internet.