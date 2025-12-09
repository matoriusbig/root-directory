# 01 - Comunicación en Red: Los 3 Pilares Fundamentales 🌐

> **🎯 Objetivo:** Entenderás cómo viajan realmente los datos a través de internet y redes locales. Dominarás la "Santa Trinidad" de las redes: Direcciones MAC, Direcciones IP y Puertos, conocimientos vitales para cualquier hacker ético o analista de redes.

-----

### 1\. La Base de Todo: Los 3 Componentes Críticos

Para que una red funcione y la comunicación fluya, necesitamos tres elementos cruciales. Sin ellos, internet sería un caos de datos perdidos. Estos son:

1.  **Direcciones MAC** (Identidad física).
2.  **Direcciones IP** (Identidad lógica/ubicación).
3.  **Puertos** (Servicio específico).

Imagina que quieres enviar una carta confidencial a un CEO específico en un edificio gigante de oficinas.

  * La **Dirección IP** es la dirección de la calle del edificio.
  * El **Puerto** es el número de la oficina específica dentro del edificio.
  * La **Dirección MAC** es la identidad física e inmutable del destinatario (su ADN o huella digital) para asegurarte de que se la das a la persona correcta en la recepción.

-----

### 2\. Direcciones MAC: La Huella Digital del Hardware 🆔

#### ¿Qué es una Dirección MAC?

La **Media Access Control (MAC)** es un identificador único asignado a la tarjeta de interfaz de red (**NIC**) de un dispositivo.

  * **Capa del Modelo OSI:** Opera en la **Capa 2 (Enlace de Datos)**.
  * **Función:** Es vital para la comunicación dentro de una red local (**LAN**). Asegura que los datos lleguen al dispositivo físico correcto.

**Estructura:**
Son 48 bits, representados en hexadecimal (ej: `00:1A:2B:3C:4D:5E`).

> **🖼️ Referencia Visual:**
>
>   * **Descripción:** Un diagrama que divida una dirección MAC en dos partes: los primeros 3 bytes como OUI (Fabricante) y los últimos 3 bytes como ID del Dispositivo.

  * **Primeros 24 bits (OUI):** Identificador Único Organizacional. Es el código del fabricante (ej: Dell, Apple, Cisco).
  * **Últimos 24 bits:** Específicos del dispositivo (como el número de serie).

> **💡 Nota:** En Windows, puedes usar el comando `GETMAC` en la terminal para ver tu dirección física.

#### ¿Cómo funciona la Magia en la LAN?

Cuando envías datos dentro de tu red local, tu computadora empaqueta la información en una **Trama (Frame)**. Aquí ocurre algo crítico:

1.  Los **Switches (Conmutadores)** usan la dirección MAC para saber a qué cable/puerto físico enviar los datos.
2.  Existe un protocolo llamado **ARP (Address Resolution Protocol)**.

**La Analogía del Salón de Clases:**

> Imagina que el profesor (Switch) tiene una carta para "Juan Pérez" (IP). Pero el profesor no sabe dónde está sentado Juan. El profesor grita: "¿Quién es Juan Pérez?". Juan levanta la mano y dice "¡Soy yo, aquí estoy\!" (Esta respuesta es su MAC). Ahora el profesor puede caminar directamente a su pupitre y entregar la carta.

> **🛡️ Nota de Seguridad:** Aquí es donde ocurre el ataque **ARP Spoofing** (o ARP Poisoning). Un atacante puede mentir y decir "¡Yo soy Juan Pérez\!" (dando su propia MAC). El Switch le enviará los datos al atacante en lugar de a la víctima.

-----

### 3\. Direcciones IP: El GPS de Internet 📍

#### ¿Qué es una Dirección IP?

La **Internet Protocol (IP)** address es una etiqueta numérica lógica.

  * **Capa del Modelo OSI:** Opera en la **Capa 3 (Red)**.
  * **Función:** Permite que los dispositivos se localicen a través de diferentes redes (como Internet).
  * **Diferencia Clave:** A diferencia de la MAC (que es permanente en el hardware), la IP puede cambiar dependiendo de a qué red te conectes.

#### Los Dos Gigantes: IPv4 vs IPv6

El mundo se quedó sin direcciones IPv4, por lo que nació IPv6. Veamos las diferencias:

| Característica | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Longitud** | 32 bits | 128 bits |
| **Formato** | Decimal (4 grupos) | Hexadecimal (8 grupos) |
| **Ejemplo** | `192.168.1.1` | `2001:0db8:85a3::8a2e` |
| **Cantidad** | \~4.3 mil millones | Prácticamente infinito |

#### El Rol de los Routers

Los **Routers (Enrutadores)** usan las direcciones IP para determinar el "mejor camino" para que tus datos lleguen a su destino. Si la MAC es para moverse dentro de la oficina, la IP es para enviar el paquete de una ciudad a otra.

-----

### 4\. Puertos: Las Puertas de los Servicios 🚪

#### ¿Qué es un Puerto?

Un puerto es un número que le dice a tu computadora qué **aplicación** o proceso debe recibir los datos.

  * **Capa del Modelo OSI:** Opera en la **Capa 4 (Transporte)**, trabajando con protocolos como TCP y UDP.

Imagina que tu dirección IP lleva el paquete al servidor correcto (el edificio). Pero en ese servidor hay muchas cosas corriendo: un sitio web, un correo electrónico, una base de datos. ¿Cómo sabe el servidor a quién entregarle el paquete? **Por el número de Puerto.**

#### Las 3 Categorías de Puertos

El rango va de 0 a 65535. Vamos a desglosarlos:

1.  **Puertos Bien Conocidos (Well-Known) [0 - 1023]:**

      * Son los "VIP". Reservados para servicios universales.
      * **Puerto 80:** HTTP (Web no segura).
      * **Puerto 443:** HTTPS (Web segura).
      * **Puerto 20/21:** FTP (Transferencia de archivos).
      * *Tu navegador usa estos automáticamente, por eso no escribes `google.com:443`.*

2.  **Puertos Registrados [1024 - 49151]:**

      * Menos estrictos, usados por aplicaciones que instalas.
      * Ejemplo: Microsoft SQL Server usa el **1433**.

3.  **Puertos Dinámicos/Privados [49152 - 65535]:**

      * Son efímeros (temporales).
      * Cuando tú (el cliente) abres una página web, tu computadora elige uno de estos puertos al azar (ej: 50432) para recibir la respuesta del servidor. Al cerrar la pestaña, el puerto se cierra.

> **💡 Nota:** Puedes usar la herramienta `netstat` en tu línea de comandos para ver qué puertos están abiertos y escuchando en tu máquina.

-----

### 5\. El Viaje de un Paquete: Ejemplo de Navegación Web 🌍

Para consolidar todo, veamos qué pasa paso a paso cuando entras a `example.com`:

1.  **DNS Lookup (La Guía Telefónica):**
    Tu computadora pregunta: "¿Cuál es la IP de example.com?". El servidor DNS responde: `93.184.216.34`.
2.  **Encapsulación de Datos:**
      * Tu navegador crea una solicitud HTTP.
      * Le pone un "sobre" TCP indicando el **Puerto de destino 80 o 443**.
      * Le pone otro "sobre" IP con la dirección `93.184.216.34`.
      * Finalmente, usa **ARP** para encontrar la **MAC** de tu Router (Gateway) para salir de casa.
3.  **Transmisión:**
    La trama viaja a tu Router (usando MAC). El Router la envía a internet (usando IP).
4.  **Procesamiento en el Servidor:**
    El servidor recibe el paquete, ve que va al puerto 443, y se lo pasa al software del Servidor Web.
5.  **Respuesta:**
    El servidor responde enviando los datos de vuelta a tu IP y a tu **Puerto Dinámico** temporal.

> **🖼️ Referencia Visual:**
>
>   * **Descripción:** Un diagrama de flujo numerado del 1 al 5 mostrando la resolución DNS, la encapsulación (cajas dentro de cajas), el viaje por la nube y la llegada al servidor.

-----

### 🎓 Resumen para llevar

  * **MAC (Capa 2):** Identidad física (Hardware). Se usa en la red local (LAN) con Switches. Formato Hexadecimal de 48 bits.
  * **IP (Capa 3):** Dirección lógica (Ubicación). Se usa para enrutamiento global con Routers. IPv4 (32 bits) y IPv6 (128 bits).
  * **Puertos (Capa 4):** Identifican el servicio/aplicación específico (HTTP, SQL, etc.).
  * **ARP:** Es el traductor que conecta el mundo lógico (IP) con el físico (MAC).
  * **Puertos Importantes:** 80 (HTTP), 443 (HTTPS), 20/21 (FTP).

-----

### Comprobación de conocimientos 🧠
Asegúrate de haber entendido los conceptos antes de seguir. Intenta responder sin mirar arriba.

1. ¿Qué protocolo es el encargado de mapear o traducir una dirección IP a una dirección MAC física?

<details> <summary><strong>Ver Respuesta</strong></summary>

ARP (Address Resolution Protocol). Es el puente vital entre la Capa 3 (IP) y la Capa 2 (MAC) en una red local.

</details>

2. ¿Qué versión de dirección IP utiliza un espacio de direccionamiento de 128 bits para solucionar la escasez de direcciones?

<details> <summary><strong>Ver Respuesta</strong></summary>

IPv6. Fue creada porque las direcciones IPv4 (32 bits) se estaban agotando.

</details>

3. ¿En qué capa del modelo OSI operan los Puertos?

<details> <summary><strong>Ver Respuesta</strong></summary>

Transport Layer (Capa de Transporte / Capa 4). Aquí es donde protocolos como TCP y UDP gestionan los puertos.

</details>

4. Si estás navegando por un sitio web seguro (candado en la barra), ¿cuál es el número de puerto estándar que está utilizando el servidor?

<details> <summary><strong>Ver Respuesta</strong></summary>

443. Es el puerto estándar para HTTPS. (El puerto 80 es para HTTP no seguro).

</details>

5. ¿Cuál es el primer paso técnico que realiza tu computadora al intentar acceder a un sitio web por su nombre (ej: https://www.google.com/search?q=google.com)?

<details> <summary><strong>Ver Respuesta</strong></summary>

DNS Lookup (Búsqueda DNS). Tu computadora necesita traducir el nombre humano a una dirección IP antes de poder enviar cualquier paquete.

</details>

6. ¿Cómo se llaman los puertos (rango 49152-65535) que tu computadora elige temporalmente para recibir respuestas de un servidor?

<details> <summary><strong>Ver Respuesta</strong></summary>

Puertos Dinámicos (o Efímeros/Privados). Se abren para una sesión y se cierran al terminar.

</details>
