# 7 - Sistema de Nombres de Dominio (DNS) 🌐

> **🎯 Objetivo:** Entender el sistema vital que hace que Internet sea navegable para los humanos. Aprenderás cómo una dirección legible como "https://www.google.com/url?sa=E\&source=gmail\&q=google.com" se convierte mágicamente en una dirección numérica que las computadoras pueden entender.

-----

### 1\. El Directorio Telefónico de Internet 📒

Imagina que para llamar a tu madre, en lugar de buscar "Mamá" en tu celular, tuvieras que marcar de memoria `+56 9 1234 5678` cada vez. Ahora imagina hacer eso para **cada sitio web** que visitas. Sería imposible, ¿verdad?

Aquí es donde entra el **DNS (Domain Name System)**.

> **💡 La Analogía:**
> El DNS es el **directorio telefónico** de Internet.
>
>   * Nosotros (humanos) preferimos nombres amigables (ej: `google.com`).
>   * Las computadoras prefieren números precisos (Direcciones IP).
>
> El DNS es el puente traductor entre nuestro lenguaje y el de las máquinas. Sin él, tendríamos que memorizar IPs como `93.184.216.34` para ver un simple ejemplo.

#### ⚔️ Nombres de Dominio vs. Direcciones IP

Aquí te muestro la diferencia clave:

| Dirección | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Nombre de Dominio** | Una dirección legible por humanos, fácil de recordar y escribir. | `www.example.com` |
| **Dirección IP** | Una etiqueta numérica que identifica el dispositivo real en la red. | `93.184.216.34` |

-----

### 2\. La Jerarquía del DNS: El Árbol Invertido 🌳

El DNS no es una lista plana; está organizado como un árbol genealógico o una jerarquía estricta que se lee de derecha a izquierda.

  * **Root Servers (Servidores Raíz) 🌱:** Son la cima de la jerarquía (aunque se representan arriba, piensa en la raíz). Son los jefes supremos que saben dónde empieza todo.
  * **TLDs (Top-Level Domains) 🔝:** Son las extensiones al final del nombre.
      * Ejemplos: `.com`, `.org`, `.net`.
      * Códigos de país: `.uk`, `.de`, `.es`.
  * **Second-Level Domains (Dominios de Segundo Nivel) 🏢:** Es el nombre de la organización o sitio.
      * Ejemplo: En `example.com`, la palabra `example` es el dominio de segundo nivel.
  * **Subdominios o Hostnames 🏘️:** Son las divisiones dentro de ese sitio.
      * Ejemplo: `www` en `www.example.com`.
      * Ejemplo: `accounts` en `accounts.google.com`.

-----

### 3\. El Proceso de Resolución: Una Carrera de Relevos 🏃‍♂️💨

Cuando escribes una dirección web y presionas Enter, ocurre un proceso fascinante llamado **Resolución DNS (DNS Resolution)**. Ocurre en fracciones de segundo, pero involucra a varios actores.

Imagina que le pides a un asistente (tu computadora) que busque una dirección.

**Paso a Paso:**

1.  **La Petición:** Escribes `www.example.com` en tu navegador.
2.  **La Memoria Corta (Caché Local):** Tu computadora primero se revisa los bolsillos. Mira su **DNS cache local** para ver si ya visitaste ese sitio recientemente y recuerda la IP.
3.  **El Ayudante (Recursive Server):** Si no está en caché, tu computadora le grita a su ayudante externo: el **Recursive DNS Server** (usualmente proporcionado por tu **ISP** o servicios como Google DNS `8.8.8.8`). Este servidor asume la responsabilidad de buscar la respuesta por ti.
4.  **Preguntando al Jefe (Root Server):** El servidor recursivo no sabe la IP, así que va al **Root Server**. El Root Server dice: *"No sé la IP exacta, pero sé quién maneja los `.com`. Ve a hablar con el servidor TLD"*.
5.  **El Especialista (TLD Name Server):** El servidor recursivo va al servidor que maneja todos los `.com`. Este servidor dice: *"No tengo la IP de la página, pero sé quién es el dueño de `example.com`. Ve al servidor autoritativo"*.
6.  **La Fuente de la Verdad (Authoritative Name Server):** Finalmente, el servidor recursivo llega al servidor DNS de la empresa `example.com`. Este servidor dice: *"¡Sí\! La dirección de `www` es `93.184.216.34`"*.
7.  **Entrega Final:** El servidor recursivo vuelve corriendo a tu computadora con la IP. Tu navegador ahora puede conectar directamente con el servidor web.

<img width="841" height="346" alt="image" src="https://github.com/user-attachments/assets/3ec2a5e3-127c-47c4-aa34-d4154690fcb2" />


> **🛡️ Nota de Seguridad:** Los atacantes a veces intentan envenenar este proceso (DNS Spoofing) para que cuando pidas `banco.com`, el servidor te dé la IP de un sitio falso. Por eso la integridad del DNS es vital.

-----

### 🎓 Resumen para llevar

  * **DNS es el traductor:** Convierte nombres humanos (`google.com`) en números de máquina (IPs).
  * **Jerárquico:** Funciona por niveles (Root -\> TLD -\> Dominio -\> Subdominio).
  * **Caché es Rey:** Para no repetir todo el proceso de los 7 pasos cada vez, tu computadora guarda las respuestas un tiempo (caché).
  * **Recursivo vs Autoritativo:** El servidor recursivo (ISP) es el que busca; el autoritativo es el que tiene la respuesta final.

-----

### Comprobación de conocimientos 🧠

¡Demuestra que eres un maestro del DNS respondiendo estas preguntas\!
1. ¿Qué tipo de dominio se considera .com?

<details> <summary><strong>Ver Respuesta</strong></summary>

Top-Level Domain: Es el dominio de nivel superior en la jerarquía.

</details>

2. En el dominio www.example.com, ¿cómo se llama a example?

<details> <summary><strong>Ver Respuesta</strong></summary>

Second-Level Domain: Es el dominio de segundo nivel, generalmente el nombre de la entidad.

</details>

3. ¿Qué es lo primero que se verifica en el proceso de resolución de DNS cuando ingresas un nombre de dominio en un navegador?

<details> <summary><strong>Ver Respuesta</strong></summary>

Local DNS cache: Tu computadora siempre revisa su memoria local antes de salir a Internet.

</details>

4. ¿Qué tipo de servidor DNS suele proporcionar un proveedor de servicios de Internet (ISP)?

<details> <summary><strong>Ver Respuesta</strong></summary>

Recursive DNS server: Es el servidor encargado de hacer las consultas en nombre del usuario.

</details>

5. ¿Qué servidor dirige al servidor DNS recursivo al servidor de nombres TLD apropiado?

<details> <summary><strong>Ver Respuesta</strong></summary>

Root Server: El servidor raíz es quien indica dónde encontrar al encargado de los .com, .org, etc.

</details>

6. ¿Qué etiqueta numérica identifica de forma única a un dispositivo en una red?

<details> <summary><strong>Ver Respuesta</strong></summary>

IP Address: Es la dirección real que necesita la máquina para comunicarse.

</details>

7. En la URL "accounts.https://www.google.com/url?sa=E&source=gmail&q=google.com", ¿cómo se considera a accounts?

<details> <summary><strong>Ver Respuesta</strong></summary>

Subdomain: Es una subdivisión o host específico dentro del dominio principal google.com.

</details>
