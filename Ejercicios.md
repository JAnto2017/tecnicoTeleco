# EJERCICIOS

## Ejercicio 1: Selección múltiple (Dirección válida en subred)

1. Dada la red 192.168.10.0/26:

    - ¿Cuál de las siguientes direcciones es válida para asignar a un host?
        - a. 192.168.10.0
        - b. 192.168.10.63
        - c. 192.168.10.45
        - d. 192.168.10.64

_Indicaciones_: Justifica por qué cada opción es válida o inválida considerando los límites de la subred.

## Ejercicio 2: Desarrollo (División en subredes)

1. Divide la red 10.0.0.0/8 en 32 subredes de igual tamaño.

    a. ¿Cuál será la nueva máscara de subred?
    b. Proporciona las direcciones de red y broadcast de las primeras dos subredes.

_Indicaciones_:

- Explica cómo determinaste la nueva máscara.
- Recuerda que el número de subredes debe ser una potencia de 2.

## Ejercicio 3: Verdadero o falso (Direcciones IP y máscaras)

1. En una red con máscara /30, solo hay dos direcciones válidas para hosts.
2. La dirección IP 192.168.0.255 siempre es una dirección de broadcast.
3. La máscara de subred 255.255.254.0 equivale a /23.
4. Si una IP tiene máscara /28, se pueden tener un máximo de 14 hosts válidos en la subred.

_Indicaciones_: Justifica cada respuesta, indicando por qué es verdadera o falsa.

## Ejercicio 4: Selección múltiple (Rango de direcciones privadas)

Selecciona la afirmación correcta:

1. ¿Cuál de las siguientes direcciones pertenece al rango de direcciones privadas?
    - a. 172.15.0.1
    - b. 192.168.100.1
    - c. 8.8.8.8
    - d. 10.255.255.255

_Indicaciones_: Explica el rango de direcciones privadas para justificar tu elección.

## Ejercicio 5: Desarrollo (Asignación de direcciones en subred)

En una empresa se asigna la red 192.168.1.0/24 para su uso interno. Esta red debe dividirse en 6 subredes, de tal manera que cada subred soporte al menos 30 hosts válidos.

1. ¿Cuál será la nueva máscara de subred?
2. Proporciona las direcciones de red y broadcast de cada subred.
3. ¿Qué subred incluirá la dirección 192.168.1.78?

_Indicaciones_:

- Muestra los cálculos para determinar la máscara de subred.
- Explica cómo verificaste que 192.168.1.78 pertenece a una subred específica.

## Soluciones y análisis

```txt
Ejercicio 1: Selección múltiple (Dirección válida en subred)
Red: 192.168.10.0/26

Máscara de subred: /26 equivale a 255.255.255.192. Esto divide la red en bloques de 64 direcciones:
Primera subred: 192.168.10.0 a 192.168.10.63
Segunda subred: 192.168.10.64 a 192.168.10.127
Solución:
192.168.10.0 → No válida, es la dirección de red de la primera subred.
192.168.10.63 → No válida, es la dirección de broadcast de la primera subred.
192.168.10.45 → Válida, está dentro del rango de hosts de la primera subred.
192.168.10.64 → No válida, es la dirección de red de la segunda subred.
Respuesta correcta: c. 192.168.10.45
```

```txt
Ejercicio 2: Desarrollo (División en subredes)
Red: 10.0.0.0/8

Dividir en 32 subredes.
Cálculo de la nueva máscara:

Número de subredes necesarias: 32.
Fórmula: 2^n ≥32, donde 𝑛 es el número de bits adicionales para subredes.

n=5 (porque 2^5 =32).
Nueva máscara: /13 (originalmente /8 + 5 bits).
Direcciones de red y broadcast de las primeras dos subredes:

Primera subred:
Red: 10.0.0.0
Broadcast: 10.7.255.255 (8 bloques = 2^(32−13)  = 524,288 direcciones por subred).
Segunda subred:
Red: 10.8.0.0
Broadcast: 10.15.255.255.
```

```txt
Ejercicio 3: Verdadero o falso (Direcciones IP y máscaras)
"En una red con máscara /30, solo hay dos direcciones válidas para hosts."

Falso. Una máscara /30 (255.255.255.252) tiene 4 direcciones en total:
1 para la red.
2 válidas para hosts.
1 para broadcast.
"La dirección IP 192.168.0.255 siempre es una dirección de broadcast."

Falso. Esto depende de la máscara de subred. Por ejemplo, en una red 192.168.0.0/23, 192.168.0.255 es una dirección válida de host.
"La máscara de subred 255.255.254.0 equivale a /23."

Verdadero. Esta máscara deja 9 bits disponibles para hosts: 32−23=9.
"Si una IP tiene máscara /28, se pueden tener un máximo de 14 hosts válidos en la subred."

Verdadero. Una máscara /28 (255.255.255.240) tiene 16 direcciones totales:
1 para red.
1 para broadcast.
16−2=14 válidas para hosts.
```

```txt
Ejercicio 4: Selección múltiple (Rango de direcciones privadas)
Opciones:

172.15.0.1 → Incorrecta. Fuera del rango privado, que es de 172.16.0.0 a 172.31.255.255.
192.168.100.1 → Correcta. Dentro del rango privado 192.168.0.0/16.
8.8.8.8 → Incorrecta. Es una dirección pública (DNS de Google).
10.255.255.255 → Correcta. Dentro del rango privado 10.0.0.0/8.
Respuesta correcta: b) 192.168.100.1 y d) 10.255.255.255
```

```txt
Ejercicio 5: Desarrollo (Asignación de direcciones en subred)
Red: 192.168.1.0/24, dividir en 6 subredes con al menos 30 hosts.

Cálculo de la nueva máscara de subred:

Hosts necesarios por subred: 30.
Fórmula: 2^n − 2 ≥ 30, donde 𝑛 es el número de bits para hosts.
n=5 (porque 2^5 − 2 = 30).
Bloques de 2^5 = 32 direcciones por subred.
Nueva máscara: /27 (originalmente /24 + 3 bits).
Direcciones de red y broadcast:

Primera subred:
Red: 192.168.1.0
Broadcast: 192.168.1.31
Segunda subred:
Red: 192.168.1.32
Broadcast: 192.168.1.63
Tercera subred:
Red: 192.168.1.64
Broadcast: 192.168.1.95
(y así sucesivamente).
¿Qué subred incluye la dirección 192.168.1.78?

Pertenece a la tercera subred:
Rango de direcciones: 192.168.1.64 a 192.168.1.95.
```
