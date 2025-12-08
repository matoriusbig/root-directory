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
    
![[OSI.png]]

---

### 3. El Modelo TCP/IP: La Realidad de Internet 🌍

Si el OSI es la teoría, el **TCP/IP** es la práctica. Es una versión condensada de 4 capas que es la que realmente usamos en Internet.

![[TCP_IP.png]]

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
    

![[modos-transmision.jpg]]

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
    
