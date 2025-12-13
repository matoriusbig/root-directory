# 09 - Redes Inalámbricas (Wireless Networks) 📡

> **🎯 Objetivo:** Cortar el "cordón umbilical" de los cables. Entenderás cómo viajan los datos por el aire, desde el router de tu casa hasta las torres gigantes en la carretera, y por qué a veces tu Wi-Fi es más lento en la cocina.

-----

### 1\. La Magia de lo Invisible 🌬️

Una **red inalámbrica** es un sistema sofisticado que usa **ondas de radio** (radio waves) para conectar dispositivos. Olvídate del cobre; aquí usamos el aire. Esto permite que tu laptop, smartphone y refrigerador inteligente "hablen" entre sí y salgan a internet sin estar atados a la pared.

> **💡 La Analogía:**
> Imagina una conversación.
>
>   * **Red Cableada:** Es como hablar por un teléfono de lata con un hilo tenso. La conexión es segura y privada, pero no te puedes mover.
>   * **Red Inalámbrica:** Es como hablar en una habitación llena de gente. Eres libre de moverte, pero cualquiera cerca puede intentar escuchar (si no hablas en clave) y el ruido de otros puede interrumpirte.

#### ⚖️ Ventajas vs. Desventajas

No todo es color de rosa. Aquí tienes el balance real:

| Ventaja (Luz ☀️) | Descripción |
| :--- | :--- |
| **Movilidad** | Puedes caminar por toda la casa o la oficina sin perder conexión. |
| **Instalación Fácil** | Olvídate de taladrar paredes para pasar cables Ethernet. |
| **Escalabilidad** | ¿Tienes un dispositivo nuevo? Solo conéctalo. No necesitas comprar más cables ni switches. |

| Desventaja (Sombra 🌑) | Descripción |
| :--- | :--- |
| **Interferencia** | Paredes, microondas y teléfonos de bebé pueden "ensuciar" la señal. |
| **Riesgos de Seguridad** | Las ondas viajan fuera de tu casa. Sin encriptación, es fácil interceptar datos. |
| **Velocidad** | Generalmente, el aire es más lento e inestable que un buen cable. |

> **🛡️ Nota de Seguridad:** Al viajar por el aire, las señales inalámbricas son susceptibles a ataques como el **"Evil Twin"** (Gemelo Malvado), donde un hacker crea una red Wi-Fi falsa con el mismo nombre que la tuya para robar tus credenciales.

-----

### 2\. El Corazón del Hogar: El Wireless Router 🏠

En casa, solemos llamar "Router" a la caja que nos da internet, pero técnicamente es un **dispositivo 2 en 1**.

1.  **Función de Router:** Dirige el tráfico (es el policía de tránsito que dice "tú vas a Google, tú vas a la impresora").
2.  **Función de Wireless Access Point (WAP):** Es la antena que convierte los datos cableados en ondas de radio para crear la zona Wi-Fi.

<img width="565" height="462" alt="image" src="https://github.com/user-attachments/assets/c6579225-8e65-48fb-91ed-9d05e14edc4c" />

**Sus componentes vitales:**

  * **Puerto WAN (Wide Area Network):** El puerto "especial" (a veces de otro color) que conecta con el mundo exterior (tu ISP).
  * **Puertos LAN:** Para conectar cosas por cable cuando necesitas velocidad máxima (ej: tu PC gamer).
  * **Antenas:** Las "bocas y oídos" del router.
  * **Procesador y Memoria:** Sí, tu router es una mini-computadora que gestiona miles de paquetes por segundo.

-----

### 3\. Internet en tu Bolsillo: Mobile Hotspot 📱

Un **Mobile Hotspot** convierte tu teléfono en un mini-router de emergencia.

  * **¿Cómo funciona?** Tu celular toma la señal **4G o 5G** (datos móviles) y la retransmite como una señal **Wi-Fi** local.
  * **El Sacrificio:** La batería de tu celular morirá rápido y el rango es muy corto (apenas unos metros).

> **Imagina que...** Estás en un aeropuerto y el Wi-Fi público no funciona (o no confías en él). Activas el Hotspot, y tu celular se convierte en el puente seguro entre tu laptop e Internet.

<img width="739" height="324" alt="image" src="https://github.com/user-attachments/assets/b921e54d-d0d8-48e3-b3fe-a195225ff32f" />

-----

### 4\. Los Gigantes: Cell Towers (Torres Celulares) 🗼

Cuando sales de casa, dejas el Wi-Fi y entras al dominio de las **Cell Towers**.

Una "Celda" (Cell) es el área geográfica cubierta por una torre. Tu teléfono es un nómada que salta de celda en celda.

**¿Cómo funciona este ecosistema?**

1.  **La Torre:** Tiene transmisores y receptores de radio potentes.
2.  **BSC (Base Station Controller):** Es el "jefe" que maneja varias torres. Decide cuándo pasarte de una torre a otra sin que se corte tu llamada (**Handoff**).
3.  **Backhaul:** Es la conexión por cable (fibra óptica) o microondas que conecta la torre con el núcleo central de Internet.

**Tipos de Celdas:**

  * **Macro Celdas:** Torres grandes para cubrir kilómetros (ideal para zonas rurales o carreteras).
  * **Micro/Small Celdas:** Pequeñas antenas en postes de luz o edificios para zonas urbanas densas donde mucha gente se conecta a la vez.

<img width="1016" height="546" alt="image" src="https://github.com/user-attachments/assets/c80eb950-c735-4ac9-80b5-4b9e1679bbdd" />

-----

### 5\. Las Carreteras Invisibles: Frecuencias 〰️

Las ondas de radio vibran a diferentes velocidades. A esto le llamamos **Frecuencia** (medida en Hertz/Hz).

Aquí está la regla de oro de la física inalámbrica:

> **💡 Regla de Oro:**
>
>   * **Frecuencia BAJA:** Viaja lejos y atraviesa paredes, pero carga menos datos (es lenta).
>   * **Frecuencia ALTA:** Es muy rápida, pero no atraviesa bien las paredes y llega cerca.

<img width="892" height="490" alt="image" src="https://github.com/user-attachments/assets/7f7120de-87b8-4712-a706-031094e4d4dc" />


#### Comparativa de Bandas

| Banda | Uso | Características | Analogía |
| :--- | :--- | :--- | :--- |
| **2.4 GHz** | Wi-Fi Viejo (802.11b/g/n) | **Rompe-muros.** Mejor alcance, pero mucha interferencia (microondas, Bluetooth). | Un sonido grave (bajo) que escuchas a través de las paredes del vecino. |
| **5 GHz** | Wi-Fi Moderno (802.11ac/ax) | **Velocidad Pura.** Rápido, pero si te alejas dos habitaciones, la señal cae. | Un susurro rápido; si cierras la puerta, no lo oyes. |
| **Celular** | 4G/5G | Varía desde 700 MHz (largo alcance) hasta 28 GHz (5G ultra rápido en estadios). | Una mezcla de ambas estrategias. |

<img width="800" height="368" alt="image" src="https://github.com/user-attachments/assets/c9ef6f49-8ebd-4a7c-9963-2b27a06a8754" />

> **Nota Técnica:** Las agencias gubernamentales (como la FCC en EE.UU.) son los "policías del aire" que deciden qué frecuencias son legales para evitar que tu Wi-Fi interfiera con los radares de los aviones.

-----

### 🎓 Resumen para llevar

  * **Sin cables:** Usamos ondas de radio. Ganamos movilidad, perdemos algo de seguridad y estabilidad.
  * **Router Casero:** Es un Router + Antena Wi-Fi en una sola caja.
  * **Hotspot:** Tu celular usando datos móviles para dar Wi-Fi a otros. Batería = 💀.
  * **Celdas:** Internet móvil funciona mediante un mosaico de torres (Macro y Micro) controladas por BSCs.
  * **2.4 GHz vs 5 GHz:** ¿Quieres atravesar paredes? Usa 2.4. ¿Quieres velocidad cerca del router? Usa 5.

-----

### Comprobación de conocimientos 🧠

¡Pon a prueba tu conexión mental!

1. ¿Qué tipo de ondas utilizan las redes inalámbricas para conectar dispositivos?

<details> <summary><strong>Ver Respuesta</strong></summary>

Radio waves (Ondas de radio): Son el medio físico invisible por el que viajan los datos.

</details>

2. ¿Qué dispositivo combina las funciones de enrutamiento y provisión de cobertura Wi-Fi en una red doméstica?

<details> <summary><strong>Ver Respuesta</strong></summary>

Wireless Router (Enrutador inalámbrico): Actúa como punto de acceso y director de tráfico a la vez.

</details>

3. ¿Qué utiliza un punto de acceso móvil (hotspot) para conectar dispositivos a Internet?

<details> <summary><strong>Ver Respuesta</strong></summary>

Cellular data (Datos móviles): Utiliza la red 4G o 5G del proveedor de telefonía para salir a internet.

</details>

4. ¿Qué estructura soporta antenas y equipos de comunicación para crear cobertura de red celular?

<details> <summary><strong>Ver Respuesta</strong></summary>

Cell Tower (Torre celular): También conocido como sitio celular, crea el área de cobertura o "celda".

</details>

5. ¿Qué gestiona múltiples torres celulares en las redes móviles?

<details> <summary><strong>Ver Respuesta</strong></summary>

Base Station Controller (BSC): Es el cerebro que coordina el traspaso de llamadas entre torres.

</details>

6. ¿Qué banda de frecuencia es conocida por una mejor penetración en las paredes pero es más propensa a las interferencias?

<details> <summary><strong>Ver Respuesta</strong></summary>

2.4 GHz: Es la frecuencia clásica, con gran alcance pero muy congestionada por otros aparatos.

</details>
