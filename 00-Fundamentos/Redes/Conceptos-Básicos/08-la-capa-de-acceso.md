# 🌐Conceptos Básicos de Red: La Capa de Acceso 


Bienvenido a esta guía introductoria sobre cómo se comunican los dispositivos en una red local. Aquí desglosamos conceptos complejos como la **Encapsulación**, las **Tramas Ethernet** y el funcionamiento lógico de un **Switch**.

**Nota:** 🧠 En ciberseguridad, la mayoría de los ataques de red local (como el *ARP Spoofing* o el *MAC Flooding*) explotan exactamente estos mecanismos que vas a aprender hoy. ¡Préstales mucha atención!


## 1. Encapsulación: El Arte de Enviar Mensajes ✉️

Para que las computadoras se entiendan, deben seguir reglas estrictas. Imagina que intentas enviar una carta sin sobre, sin dirección y escrita en un idioma inventado. Nadie la recibiría. En redes, pasa lo mismo.

### **¿Qué es la Encapsulación?**

Es el proceso de **meter un mensaje dentro de otro formato** para que pueda ser entregado.

- **Encapsulamiento:** Meter la carta en el sobre.

- **Desencapsulamiento:** Sacar la carta del sobre al recibirla.

### **La Analogía de la Carta y el Sobre 📨**
<img width="416" height="458" alt="image" src="https://github.com/user-attachments/assets/d8ca1575-90f9-49fa-8703-9fcbb7ef01ad" />
<img width="592" height="315" alt="image" src="https://github.com/user-attachments/assets/6c6df0c7-d213-47f6-aa79-c9fe5eae1dc1" />

*En la imagen anterior vemos una carta física. Para enviarla, no basta con el papel escrito; necesitamos un sobre con la dirección de origen (remitente) y destino.*

#### **📊 Comparativa Carta vs. Trama Digital**

Esta tabla compara los elementos de un correo postal con los de una trama de red.

| Elemento de la Carta (Analógico) | Elemento de la Trama (Digital) | Función |
|---|---|---|
| Destinatario (1400 Main Street...) | Dirección MAC de Destino | ¿A quién va dirigido el mensaje? |
| Remitente (4085 SE Pine Street...) | Dirección MAC de Origen | ¿Quién escribió el mensaje? |
| Saludo ("Querida Jane") | Preámbulo / Inicio de Trama | Alerta al receptor de que viene un mensaje. |
| Contenido de la carta ("Acabo de regresar...") | Datos Encapsulados (Carga útil) | El mensaje real (puede ser una foto, un email, etc.). |
| Fin de la carta / Sello | Fin de la trama (FCS) | Indica que el mensaje terminó y verifica que llegó bien. |


## 2. La Trama Ethernet (Ethernet Frame) 📦

En la capa de acceso (Capa 2 del modelo OSI), los datos no viajan "sueltos", viajan dentro de una **Trama Ethernet**. Piensa en la trama como el "vagón" que transporta tu información por el cable.

La estructura de este vagón es la siguiente:

1. **Preámbulo (8 bytes):**

- *Función:* ¡Despierta! Sirve para sincronizar la tarjeta de red (NIC) receptora con la emisora.

- **Delimitador de Inicio de Trama (SFD):**

- *Función:* Avisa: "Atención, justo después de este bit comienza la información real".

- **Dirección MAC de Destino (6 bytes):**

- *Función:* Es la identificación única de la tarjeta de red que debe recibir el paquete.

- **Dirección MAC de Origen (6 bytes):**

- *Función:* Es la identificación de quién envió el paquete.

- **Longitud / Tipo:**

- *Función:* Define dos cosas. O bien el **largo** de los datos, o el **tipo de protocolo** que viene adentro (por ejemplo, ¿es un paquete IPv4 o IPv6?).

- **Datos Encapsulados:**

- *Función:* Aquí va la carga útil. Puede ser un paquete IP, un fragmento de una web, etc. A Ethernet no le importa qué es, solo lo transporta.

- **Secuencia de Verificación de Tramas (FCS):**

- *Función:* Control de calidad. Verifica si la trama llegó dañada por interferencias en el cable.

### **🌐 Red: El Paquete IP**

Dentro del campo "Datos" de la trama Ethernet, a menudo viaja un paquete IP.
<img width="576" height="393" alt="image" src="https://github.com/user-attachments/assets/4ad9ac8c-95e8-4e23-b344-a4681b8b7fd4" />


- **Explicación de la imagen:** Esta imagen muestra un encabezado de **IPv6**. Observa que también tiene una "Dirección de Origen" y "Dirección de Destino", pero estas son direcciones IP (lógicas), no MAC (físicas).

- **Analogía:** La dirección MAC es tu dirección física (tu casa), la dirección IP es como tu número de teléfono (te pueden localizar en diferentes lugares). Ethernet usa MAC para llegar de un dispositivo a otro en la *misma* red.


## 3. El Switch Ethernet: El Cerebro de la Red Local 🧠

Antiguamente usábamos "Hubs" (concentradores), que eran tontos: si alguien hablaba, el Hub lo gritaba a todos los puertos, causando colisiones y tráfico lento.

El **Switch (Conmutador)** es inteligente. Opera en la **Capa 2** y toma decisiones basándose en las direcciones MAC.

**Nota:** Un Switch permite comunicaciones simultáneas dedicadas (circuitos) entre puertos. Si el puerto 1 habla con el 4, el puerto 2 puede hablar con el 3 al mismo tiempo sin interrumpirse.


## 4. La Tabla de Direcciones MAC (MAC Address Table) 📝

Aquí es donde ocurre la magia. El Switch tiene una memoria (tabla) donde anota qué dispositivo está conectado a qué puerto. Pero, ¿cómo aprende? Vamos a verlo con la situación de la pizarra.

### **Escenario A: Aprendizaje y "Unknown Unicast" (Inundación)**

<img width="592" height="376" alt="image" src="https://github.com/user-attachments/assets/dad30a63-0b77-463f-ae93-8949d0cf253a" />

**Situación:** La PC H1 (MAC: AA-AA) quiere enviar datos a la PC H4 (MAC: DD-DD).

- **Tabla del Switch al inicio:** Vacía o incompleta.

**Paso a paso:**

1. **El Envío:** H1 construye una trama.

- Origen: AA-AA

- Destino: DD-DD

- **Recepción y Aprendizaje (Learning):** El Switch recibe la trama en el puerto FA 0/1.

- *El Switch piensa:* "¡Ajá! Acabo de recibir algo de AA-AA por el puerto 0/1. Anotaré eso en mi tabla".

- ✅ **Tabla Actualizada:** AA-AA = Puerto FA 0/1.

- **Búsqueda (Forwarding):** El Switch mira el destino DD-DD y busca en su tabla.

- *El Switch piensa:* "¿Dónde está DD-DD? No lo tengo en mi lista..." 😟

- **Inundación (Flooding):** Como no sabe dónde está el destino (esto se llama **Unicast Desconocido**), el Switch envía la trama por **TODOS** los puertos excepto por el que entró.

- **El Resultado:**

- H2 y H3 reciben la trama, miran que es para DD-DD, dicen "no soy yo" y la descartan 🗑️.

- H4 recibe la trama, dice "¡Soy yo!" y la procesa ✅.

### **Escenario B: Respuesta y "Known Unicast" (Envío Directo)**

<img width="588" height="364" alt="image" src="https://github.com/user-attachments/assets/e6f5beb4-14b6-4192-b0db-46a508a5076f" />

Ahora miremos la continuación lógica en la pizarra completa:

**Situación:** Ahora H4 (MAC: DD-DD) quiere responderle a H1 (MAC: AA-AA).

**Paso a paso:**

1. **El Envío:** H4 crea la trama de respuesta.

- Origen: DD-DD

- Destino: AA-AA

- **Aprendizaje:** El Switch recibe la trama en el puerto FA 0/4.

- *El Switch piensa:* "Veo que DD-DD está en el puerto 0/4. Lo anoto".

- ✅ **Tabla Actualizada:**

- AA-AA en FA 0/1

- DD-DD en FA 0/4

- **Reenvío Inteligente:** El Switch mira el destino AA-AA.

- *El Switch piensa:* "¡Espera! Ya sé dónde está AA-AA. Está en el puerto 0/1".

- **Entrega Directa:** El Switch envía la trama **SOLO** por el puerto FA 0/1.

- Nadie más recibe "basura". La red es más eficiente y segura.


## Resumen de Conceptos Clave 🎓

- **Trama Ethernet:** El contenedor de datos en la capa 2. Tiene direcciones MAC de origen y destino.

- **Encapsulación:** El proceso de "empaquetar" datos (como meter una carta en un sobre).

- **Switch:** Dispositivo inteligente que conecta equipos y evita colisiones creando circuitos temporales.

- **Tabla MAC:** La base de datos del Switch. Mapea Dirección MAC -> Puerto Físico.

- **Aprendizaje (Source MAC):** El Switch aprende mirando **quién envía** (MAC de origen).

- **Reenvío (Destination MAC):** El Switch decide a dónde enviar mirando **a quién va dirigido** (MAC de destino).
