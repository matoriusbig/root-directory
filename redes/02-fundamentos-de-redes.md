# 02 - Fundamentos de Red: El Mapa del Tesoro Digital 🗺️

> **🎯 Objetivo:** Descubrirás la arquitectura invisible que sostiene Internet. Aprenderás a diferenciar el modelo teórico (OSI) del práctico (TCP/IP), y entenderás cómo fluyen los datos desde un clic en tu navegador hasta convertirse en pulsos de luz en un cable submarino.

---

### 1. El Ecosistema Oculto 🌐

A menudo damos por sentado que "Internet funciona". Pero la realidad es que cada dispositivo moderno —desde tu smartphone hasta tu refrigerador inteligente— se comunica gracias a una pila de tecnología increíblemente compleja construida sobre **TCP/IP**.

Para un experto en ciberseguridad, ver una red no es ver cables y routers; es ver capas de interacción. Vamos a desglosar cómo encaja todo esto utilizando dos modelos famosos: **OSI** y **TCP/IP**.

---

### 2. El Modelo OSI: Las 7 Capas de la Verdad 🏗️

El **Modelo OSI (Open Systems Interconnection)** es un marco conceptual. Piénsalo como la "teoría gramatical" de las redes. Divide la comunicación en 7 capas abstractas para que diferentes fabricantes puedan crear dispositivos que se entiendan entre sí.

> 💡 Analogía Maestra:
> 
> Imagina el proceso de enviar un regalo frágil por correo. Cada capa añade una protección o etiqueta (encabezado) al paquete antes de enviarlo.

Aquí están las 7 capas, desde los cables hasta tu pantalla:

#### **Capa 1: Física (Physical Layer) 🔌**

Es la base. Aquí no hay "datos", solo **bits** (unos y ceros) viajando como electricidad o luz.

- **Función:** Transmisión pura de bits a través del medio.
    
- **Hardware:** Cables Ethernet, Hubs, Repetidores.
    

#### **Capa 2: Enlace de Datos (Data Link Layer) 🔗**

Aquí los bits se organizan en "tramas". Esta capa se encarga de la entrega local (en la misma red).

- **Identificador:** Direcciones **MAC (Media Access Control)**. Es como el número de serie único de tu tarjeta de red.
    
- **Hardware:** Switches (Conmutadores) y Bridges (Puentes).
    

> **🛡️ Nota de Seguridad:** Aquí ocurren ataques como el **MAC Spoofing** o **ARP Poisoning**, donde un atacante se hace pasar por otro dispositivo en la red local.

#### **Capa 3: Red (Network Layer) 📍**

Esta capa decide "la mejor ruta" para que los datos viajen a través de diferentes redes (Internet).

- **Identificador:** Direcciones **IP (Internet Protocol)**. Es como tu dirección postal.
    
- **Hardware:** Routers.
    
- **Función:** Enrutamiento (Routing) y direccionamiento lógico.
    

#### **Capa 4: Transporte (Transport Layer) 🚚**

Se asegura de que los datos lleguen completos y al lugar correcto dentro del dispositivo.

- **Protocolos estrella:**
    
    - **TCP (Transmission Control Protocol):** Fiable. Verifica errores y reenvía si algo falta. (Ej: Cargar una web).
        
    - **UDP (User Datagram Protocol):** Rápido pero no garantiza entrega. (Ej: Streaming de video o juegos online).
        

#### **Capa 5: Sesión (Session Layer) 🤝**

Es el "semáforo" de las conversaciones. Establece, mantiene y cierra la conexión entre dos aplicaciones. Si se corta la descarga y la reanudas, agradece a esta capa.

#### **Capa 6: Presentación (Presentation Layer) 🎁**

El traductor universal. Se asegura de que los datos sean legibles.

- **Funciones:** Encriptación (hacer los datos seguros), compresión (hacerlos pequeños) y traducción de formatos.
    

#### **Capa 7: Aplicación (Application Layer) 🖥️**

Lo que tú ves. No es el programa en sí (como Chrome), sino los protocolos que el programa usa para hablar con la red.

- **Protocolos:** HTTP (Web), FTP (Archivos), SMTP (Email), DNS.
    
<img width="723" height="702" alt="OSI" src="https://github.com/user-attachments/assets/edbdb4be-7f49-4849-9078-edb8b3ebb27d" />


---

### 3. El Modelo TCP/IP: La Realidad de Internet 🌍

Si el OSI es la teoría, el **TCP/IP** es la práctica. Es una versión condensada de 4 capas que es la que realmente usamos en Internet.

<img width="765" height="580" alt="TCP_IP" src="https://github.com/user-attachments/assets/9f73b6d6-ecdc-4720-8000-0493745d6be4" />


| **Capa TCP/IP**              | **Equivalente OSI**              | **Descripción Práctica**                                               |
| ---------------------------- | -------------------------------- | ---------------------------------------------------------------------- |
| **Application (Aplicación)** | Aplicación, Presentación, Sesión | Todo lo relacionado con los datos del usuario y servicios (HTTP, FTP). |
| **Transport (Transporte)**   | Transporte                       | Garantiza la entrega de datos (TCP/UDP).                               |
| **Internet**                 | Red                              | Direccionamiento IP y enrutamiento de paquetes.                        |
| **Link (Enlace)**            | Enlace de Datos, Física          | Hardware físico, MACs, Cables y Wi-Fi.                                 |

> **💡 Nota:** Mientras que OSI es perfecto para **enseñar y diagnosticar** problemas, TCP/IP es el modelo que **construyó Internet**.

---

### 4. Protocolos: El Idioma de las Redes 🗣️

Los protocolos son simplemente reglas estrictas. Si dos dispositivos no siguen el mismo protocolo, es como si uno hablara japonés y el otro francés.

Aquí tienes los "famosos" que debes conocer:

|**Protocolo**|**Capa**|**Función "En Español"**|
|---|---|---|
|**HTTP**|Aplicación|El idioma de la Web. Entrega páginas y contenido.|
|**FTP**|Aplicación|El mensajero de archivos. Sube y baja ficheros.|
|**SMTP**|Aplicación|El cartero. Envía correos electrónicos entre servidores.|
|**TCP**|Transporte|El transportista meticuloso. Garantiza que llegue todo y en orden.|
|**UDP**|Transporte|El transportista veloz. Tira los paquetes rápido; si se cae uno, no se detiene.|
|**IP**|Internet/Red|El GPS. Lleva los paquetes de origen a destino cruzando redes.|

---

### 5. Transmisión: Cómo viaja la señal 📡

Al final del día, todo esto debe convertirse en algo físico para viajar.

#### Tipos de Transmisión

- **Analógica:** Señales continuas (como la radio antigua).
    
- **Digital:** Señales discretas (bits: 0s y 1s). Es lo que usan las computadoras modernas.
    

#### Modos de Transmisión (¿Quién habla y cuándo?)

1. **Simplex:** Solo un sentido. (Ej: Un teclado hacia la PC, o la radio del auto. Tú escuchas, no respondes).
    
2. **Half-Duplex:** Ambos hablan, pero **no al mismo tiempo**. (Ej: Walkie-Talkies "Cambio y fuera").
    
3. **Full-Duplex:** Ambos hablan y escuchan **simultáneamente**. (Ej: Una llamada telefónica o tu conexión a Internet actual).
    
![modos-transmision](https://github.com/user-attachments/assets/480f9f36-41c9-4495-95fe-55b56ae31cbe)



#### Medios de Transmisión (La Carretera)

- **Cobre (Par Trenzado/Coaxial):** Usa electricidad. Común en LANs (Ethernet).
    
- **Fibra Óptica:** Usa pulsos de luz. Extremadamente rápida, usada en el backbone de Internet.
    
- **Inalámbrico (Wi-Fi/Radio):** Usa ondas electromagnéticas.
    

---

### 🎓 Resumen para llevar

- **OSI (7 Capas) vs TCP/IP (4 Capas):** OSI es tu mapa teórico para entender y solucionar problemas; TCP/IP es la implementación real de Internet.
    
- **Las Capas Importan:** Los Routers viven en la Capa 3 (IP), los Switches en la Capa 2 (MAC). Saber esto es vital para entender dónde falla una red o dónde atacarla.
    
- **TCP vs UDP:** ¿Quieres fiabilidad (correos, web)? Usas **TCP**. ¿Quieres velocidad (streaming, llamadas)? Usas **UDP**.
    
- **Full-Duplex:** Es el estándar moderno; permite enviar y recibir datos a la vez.

-----

🧠 Comprobación de Conocimientos: OSI y TCP/IP
Ya has navegado por las capas teóricas. Ahora, vamos a ver si puedes identificar dónde encaja cada pieza del rompecabezas en el mundo real. ¡A por ello!

1. Estamos mirando los cables físicos y la electricidad. ¿Qué capa del modelo OSI es responsable de las conexiones físicas, como los cables Ethernet, y la transmisión de bits puros?

a) Network Layer (Capa de Red) b) Physical Layer (Capa Física) c) Data Link Layer (Capa de Enlace de Datos) d) Transport Layer (Capa de Transporte)

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

b) Physical Layer (Capa Física)

Explicación: Es la base de todo (Capa 1). Aquí no nos preocupamos por direcciones IP ni datos lógicos, solo nos importa el hardware: cables, voltajes, pines y luz. Si puedes tocarlo, probablemente sea Capa 1.

</details>

2. Necesitamos enviar un paquete a una dirección IP específica en otra ciudad. Nombra la capa OSI que se ocupa del direccionamiento lógico (IP) y de encontrar la mejor ruta (enrutamiento).

a) Data Link Layer (Capa de Enlace de Datos) b) Transport Layer (Capa de Transporte) c) Network Layer (Capa de Red) d) Session Layer (Capa de Sesión)

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

c) Network Layer (Capa de Red)

Explicación: La Capa 3 es el "GPS" de la red. Se encarga de las direcciones lógicas (como las IPs) y determina la ruta que deben seguir los datos a través de diferentes redes para llegar a su destino.

</details>

3. Necesitamos enviar un archivo importante y no podemos permitirnos perder ni un solo bit. ¿Qué protocolo garantiza la entrega fiable de datos, verifica que llegaron bien y opera en la Capa de Transporte?

a) UDP (User Datagram Protocol) b) IP (Internet Protocol) c) TCP (Transmission Control Protocol) d) ICMP (Internet Control Message Protocol)

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

c) TCP (Transmission Control Protocol)

Explicación: TCP es el protocolo "obsesivo". Establece una conexión, numera los paquetes y exige un recibo (ACK) por cada uno. Si algo se pierde, lo reenvía. Fiabilidad total.

</details>

4. Estás conectando computadoras en una oficina usando direcciones MAC para mover datos localmente. ¿En qué capa del modelo OSI operan principalmente los Switches (conmutadores)?

a) Layer 1 - Physical b) Layer 2 - Data Link (Enlace de Datos) c) Layer 3 - Network d) Layer 4 - Transport

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

b) Layer 2 - Data Link (Enlace de Datos)

Explicación: Los Switches tradicionales leen las direcciones físicas (MAC Addresses) para saber a qué puerto específico enviar la trama. Esto ocurre en la Capa 2.

</details>

5. El modelo TCP/IP es más simple que el OSI. ¿Qué capa del modelo TCP/IP agrupa y corresponde a las capas de Aplicación, Presentación y Sesión del modelo OSI?

a) Network Access Layer b) Internet Layer c) Transport Layer d) Application Layer

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

d) Application Layer

Explicación: El modelo TCP/IP condensa las tres capas superiores del OSI (todo lo que tiene que ver con el software, el formato y la sesión del usuario) en una sola gran capa llamada Aplicación.

</details>

6. Antes de que veas una página web segura, los datos deben descifrarse y traducirse a un formato que tu navegador entienda. ¿Qué capa del modelo OSI gestiona el cifrado de datos y la conversión de formatos?

a) Application Layer (Capa de Aplicación) b) Presentation Layer (Capa de Presentación) c) Session Layer (Capa de Sesión) d) Transport Layer (Capa de Transporte)

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

b) Presentation Layer (Capa de Presentación)

Explicación: La Capa 6 actúa como el "Traductor". Se asegura de que los datos sean legibles (formato JPEG, ASCII, etc.) y maneja el cifrado/descifrado (como SSL/TLS).

</details>

7. Estás navegando por Internet leyendo este texto. Nombra un protocolo fundamental utilizado para la navegación web que opera en la Capa de Aplicación.

a) HTTP (Hypertext Transfer Protocol) b) TCP (Transmission Control Protocol) c) IP (Internet Protocol) d) ARP (Address Resolution Protocol)

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

a) HTTP (Hypertext Transfer Protocol)

Explicación: HTTP (o su versión segura HTTPS) es el lenguaje que usan los navegadores y servidores web para comunicarse. Es lo que ves al principio de la URL y vive en la capa más alta, la de Aplicación.

</details>

8. Si un archivo grande se divide en pedazos pequeños para enviarse, alguien debe asegurarse de rearmarlos en el orden correcto al llegar. ¿Qué capa OSI asegura que los segmentos se transfieran de forma fiable y en secuencia?

a) Network Layer b) Transport Layer c) Session Layer d) Data Link Layer

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

b) Transport Layer

Explicación: La Capa 4 (Transporte) toma los datos de la aplicación, los corta en segmentos manejables y se asegura de que, en el otro extremo, se vuelvan a unir en el orden correcto, manejando el control de flujo y errores.

</details>

9. Estás viendo un streaming de video en vivo o jugando online y necesitas velocidad pura, aunque se pierdan algunos cuadros por el camino. ¿Qué protocolo proporciona una comunicación rápida y sin conexión en la Capa de Transporte?

a) TCP b) FTP c) UDP d) SSH

<details> <summary><strong>Ver Respuesta Correcta</strong></summary>

c) UDP

Explicación: UDP es el protocolo "rápido y furioso". No pierde tiempo estableciendo conexión ni verificando si los datos llegaron. Simplemente los envía. Es ideal para streaming y voz en tiempo real donde la velocidad es más importante que la perfección.

</details>

