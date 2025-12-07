# 🏗️ 4.1 - Modelo OSI y TCP/IP

En esencia, una red es simplemente **dos o más computadoras conectadas entre sí** para compartir datos, información o recursos. Para la ciberseguridad, es vital entender cómo se construyen estas "carreteras" y cómo vigilar el "tráfico".

---

## 🗺️ Tipos de Redes

* **Red de Área Local (LAN):** Una red contenida en un área geográfica pequeña (ej. tu casa, una oficina).
* **Red de Área Amplia (WAN):** Una red que conecta múltiples LAN a través de largas distancias (ej. Internet, o la red que conecta las oficinas de Santiago y Nueva York).

---

## ⚙️ Dispositivos de Red (El Hardware)

Estos son los componentes físicos que construyen y dirigen las "carreteras".

* 📣 **Concentrador (Hub):**
    * **Cómo funciona:** Cuando recibe datos, los **retransmite a todos los demás puertos**.
    * **Analogía:** Estar en una habitación y gritar un mensaje. Todos lo oyen.
    * **Impacto en Seguridad:** Muy inseguro. Facilita el "sniffing" (escuchar tráfico ajeno).
* 🚦 **Conmutador (Switch):**
    * **Cómo funciona:** "Inteligente". Aprende la **dirección MAC** de cada dispositivo y envía datos *únicamente* al puerto del destinatario.
    * **Analogía:** Un cartero eficiente que entrega el mensaje directamente al escritorio correcto.
    * **Impacto en Seguridad:** Fundamental. Permite crear **VLANs** para segmentar la red.
* 🗺️ **Enrutador (Router):**
    * **Qué es:** El dispositivo que **conecta diferentes redes entre sí** (ej. tu LAN con Internet/WAN).
    * **Cómo funciona:** Toma decisiones basadas en **direcciones IP** para encontrar la "ruta" más eficiente.
    * **Analogía:** Es el "GPS" o la "oficina de correos" de la red.
* 🛡️ **Cortafuegos (Firewall):**
    * **Qué es:** Un dispositivo de seguridad que filtra el tráfico.
    * **Cómo funciona:** Decide si permitir o bloquear el tráfico basándose en reglas predefinidas **(ACLs)**.
    * **Analogía:** El **guardia de seguridad** en la entrada de un edificio con una lista de invitados.
* 🗄️ **Servidor (Server):**
    * Una computadora diseñada para "servir" información (ej. Servidor Web, Servidor de Archivos, Servidor de Correo).
* 💻 **Punto Final (Endpoint):**
    * Cualquier dispositivo al final de un enlace (Laptops, teléfonos, impresoras, Smart TVs). A menudo es el eslabón más débil.

<img width="945" height="1142" alt="Diagrama de Dispositivos de Red" src="https://github.com/user-attachments/assets/e29ca35c-8883-46b1-9ed9-dc3caa220bff" />

---

## 🔑 Conceptos Clave de Direccionamiento

Cada dispositivo necesita dos tipos de direcciones.

* 🌎 **Dirección MAC (Control de Acceso al Medio):**
    * **Qué es:** Una dirección *física* y única, quemada en la tarjeta de red (NIC).
    * **Formato:** `00-13-02-1F-58-F5`
    * **Analogía:** El **número de serie (VIN) de un auto**. Se usa para la comunicación *dentro* de la misma LAN (trabajo del Switch).
* 📮 **Dirección IP (Protocolo de Internet):**
    * **Qué es:** Una dirección *lógica* que identifica un dispositivo en una red.
    * **Formato (IPv4):** `192.168.1.1`
    * **Analogía:** La **dirección de tu casa** (`Calle Falsa 123`). Se usa para la comunicación *entre* diferentes redes (trabajo del Router).

---

## 🏙️ Diagramas de Red (Visualizando la Conexión)

### Ejemplo 1: Red de Pequeña Empresa

<img width="479" height="370" alt="Diagrama de Red de Pequeña Empresa" src="https://github.com/user-attachments/assets/a5593f4d-e4d1-4b73-b5bc-8c3babf2057d" />

* **Flujo:** Internet ➡️ Firewall (filtra) ➡️ Switch (distribuye) ➡️ Endpoints/Servidores.

### Ejemplo 2: Red Doméstica Típica
<img width="495" height="324" alt="Captura de pantalla 2025-11-07 234036" src="https://github.com/user-attachments/assets/b14b2d6d-0852-4771-b61f-f8178c4b73b4" />

* **Diferencia Clave:** El dispositivo del ISP es un "todo en uno" (Router + Firewall + Switch + Punto de Acceso Wi-Fi).

---

## 📚 Modelos de Red (Las Reglas del Juego)

Son marcos conceptuales que dividen la comunicación en "capas".

### El Modelo OSI (Interconexión de Sistemas Abiertos)

El modelo **teórico de 7 capas**. Es tu "libro de texto".

| Capa | Nombre | Propósito Principal |
| :--- | :--- | :--- |
| **7** | **Aplicación** | Interfaz de usuario-red (HTTP, SMTP) |
| **6** | **Presentación** | Formato de datos, encriptación (SSL/TLS) |
| **5** | **Sesión** | Iniciar, mantener y terminar conexiones |
| **4** | **Transporte** | Entrega Host-a-Host (TCP/UDP) |
| **3** | **Red** | Direccionamiento y enrutamiento (IP) |
| **2** | **Enlace de Datos** | Entrega Nodo-a-Nodo (MAC, Ethernet) |
| **1** | **Física** | Transmisión de bits (cables, ondas) |

### 📦 Encapsulación y Desencapsulación

* **Encapsulación (Bajar):** Cada capa añade su propio "encabezado" (header).
    * Capa 4 (Transporte) ➡️ **Segmento** (TCP) o **Datagrama** (UDP)
    * Capa 3 (Red) ➡️ **Paquete** (IP)
    * Capa 2 (Enlace) ➡️ **Trama** (Ethernet)
* **Desencapsulación (Subir):** El receptor quita los encabezados en orden inverso.

### El Modelo TCP/IP (El Modelo Práctico)

El modelo de 4 capas que *realmente* utiliza Internet.

| Capa TCP/IP | Protocolos Clave | Capas OSI Equivalentes |
| :--- | :--- | :--- |
| **Aplicación** | HTTP, SMTP, DNS | 5, 6, 7 |
| **Transporte** | **TCP**, **UDP**, ICMP | 4 |
| **Internet** | **IP** (IPv4, IPv6) | 3 |
| **Interfaz de Red** | Ethernet, Wi-Fi | 1, 2 |

### TCP vs. UDP (Capa 4)

* **TCP (Protocolo de Control de Transmisión):** **Confiable**. Verifica que cada paquete llegue en orden. Usa el "saludo de tres vías".
    * *Uso:* Cargar sitios web, emails (debe ser perfecto).
* **UDP (Protocolo de Datagramas de Usuario):** **Rápido** pero no confiable. Simplemente "lanza" los datos.
    * *Uso:* Streaming de video, juegos, VoIP (la velocidad importa más que un píxel perdido).

---

## 7. 📮 Protocolos de Internet (IPv4 vs. IPv6)

### IPv4

* **Formato:** 32 bits (ej. `216.12.146.140`).
* **El Problema:** **Agotado** (~4.3 mil millones de direcciones).
* **Solución Temporal:** **Direcciones Privadas** (No enrutables en Internet, reutilizables en LANs).
    * `10.0.0.0 /8` (Corporativo grande)
    * `172.16.0.0 /12` (Corporativo mediano)
    * `192.168.0.0 /16` (Hogar / Pequeña oficina)
* **Loopback:** `127.0.0.1` siempre significa "esta misma máquina".

### IPv6

* **Formato:** 128 bits (ej. `2001:0db8::ffff:0:1`).
* **Beneficios:** Espacio de direcciones ilimitado; **IPsec (seguridad) está integrado**.

---

## 8. 🚪 Puertos y Protocolos (Puertas y Servicios)

* **Puerto Físico:** El enchufe en un switch.
* **Puerto Lógico (Socket):** Un número (0-65535) que actúa como una "puerta" en una IP para un servicio específico.

> **Analogía:**
> * **Dirección IP** = Dirección del edificio (`192.168.1.1`).
> * **Puerto Lógico** = Número del apartamento (`80`, `443`, `22`).

### Protocolos Seguros vs. Inseguros (Crítico)

Tu trabajo es forzar el uso de las alternativas seguras, ya que las inseguras envían datos (¡y contraseñas!) en **texto plano**.

| Puerto (Inseguro) | Protocolo | Riesgo | Puerto (Seguro) | Protocolo (Alternativa Segura) |
| :--- | :--- | :--- | :--- | :--- |
| 21 | **FTP** | Credenciales en texto plano | 22 | **SFTP** (SSH) |
| 23 | **Telnet** | Toda la sesión en texto plano | 22 | **SSH** (Secure Shell) |
| 80 | **HTTP** | Tráfico web en texto plano | 443 | **HTTPS** (HTTP sobre TLS) |
| 143 | **IMAP** | Correo y credenciales en texto plano | 993 | **IMAPS** (sobre SSL/TLS) |
| 389 | **LDAP** | Consultas de directorio en texto plano | 636 | **LDAPS** (sobre SSL/TLS) |

---

## 9. 🤝 Estableciendo la Conexión (3-Way Handshake de TCP)

Para establecer una conexión **confiable** (TCP):

1.  **[Cliente] ➡️ [Servidor]: `SYN`**
    * Cliente: "Hola, ¿puedo conectarme?"
2.  **[Servidor] ➡️ [Cliente]: `SYN-ACK`**
    * Servidor: "¡Sí! ¿Confirmas que me escuchaste?"
3.  **[Cliente] ➡️ [Servidor]: `ACK`**
    * Cliente: "Confirmado. Aquí van los datos."
