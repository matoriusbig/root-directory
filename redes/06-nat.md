# 06 - Traducción de Direcciones de Red (NAT) 🌐

> **🎯 Objetivo:** Entender cómo diablos conectamos miles de millones de dispositivos a Internet cuando las direcciones "reales" se acabaron hace años. Aprenderás cómo tu router actúa como un "traductor diplomático" entre tu casa y el mundo exterior.

-----

### 1\. El Problema: Una Escasez Digital 📉

Imagina que el mundo se quedara sin números de teléfono. Eso es exactamente lo que pasó con **IPv4**. El sistema original de direcciones IP ofrece aproximadamente **4.3 mil millones** de direcciones. Suena a mucho, ¿verdad? Pero con el crecimiento explosivo de móviles, portátiles y neveras inteligentes, nos quedamos cortos muy rápido.

Aquí entra el salvador: **NAT (Network Address Translation)**.

> **💡 Nota:** La idea central de NAT es permitir que **múltiples dispositivos** en una red privada (tu casa) compartan una **única dirección IP pública**. Es el reciclaje definitivo de direcciones.

-----

### 2\. IPs Públicas vs. Privadas: Los Dos Mundos 🌍🏠

Para entender NAT, primero debemos diferenciar los dos tipos de "carnets de identidad" en la red.

#### 🏛️ Direcciones IP Públicas

Son como tu dirección postal real. Son identificadores **únicos a nivel global** asignados por los Proveedores de Internet (ISP).

  * Son accesibles desde cualquier lugar de Internet.
  * **Ejemplo:** `8.8.8.8` (Servidor DNS de Google) o `142.251.46.174` (Servidor web de Google).

#### 🏠 Direcciones IP Privadas

Son como los nombres que usas dentro de tu casa ("Mamá", "Papá", "El perro"). Solo tienen sentido **dentro de tu red local**.

  * **No son enrutables** en Internet (si envías un paquete a una IP privada desde fuera, los routers de Internet lo descartarán).
  * Se definen en el estándar **RFC 1918**.

**Los Rangos Reservados (Memoriza esto):**

  * `10.0.0.0` a `10.255.255.255` (Redes grandes)
  * `172.16.0.0` a `172.31.255.255` (Empresas medianas)
  * `192.168.0.0` a `192.168.255.255` (Tu red doméstica típica)

> **🛡️ Nota de Seguridad:** Las IPs privadas añaden una capa de seguridad natural. Como no se pueden "ver" directamente desde Internet, tus dispositivos internos no están expuestos directamente a ataques externos, a menos que configures explícitamente el router para permitirlo.

-----

### 3\. ¿Qué es NAT? El Gran Traductor 🗣️

**Network Address Translation (NAT)** es el proceso donde un dispositivo (usualmente tu Router) modifica las cabeceras de los paquetes IP mientras pasan a través de él.

> **La Analogía de la Recepción:** 🏢
> Imagina una gran empresa. Tiene un solo número de teléfono público (IP Pública). Dentro, hay 500 empleados con extensiones internas (IPs Privadas).
>
>   * Cuando un empleado llama a un cliente, la llamada sale con el número de la empresa.
>   * Cuando el cliente devuelve la llamada, llama a la recepción (Router), y el recepcionista la desvía a la extensión correcta.
>
> ¡Eso es NAT\! Tu Router es el recepcionista.

-----

### 4\. La Magia: ¿Cómo funciona NAT paso a paso? ⚙️

Visualicemos tu red doméstica. Tienes un portátil, un smartphone y una consola.

1.  **Tu Router:** Tiene dos caras.
      * **Cara LAN (Interna):** IP `192.168.1.1` (La puerta de enlace para tus dispositivos).
      * **Cara WAN (Externa):** IP `203.0.113.50` (La cara que ve Internet).
2.  **Tu Laptop:** Tiene la IP privada `192.168.1.10`.

**El Viaje del Paquete:**

1.  **Petición:** Tu laptop quiere ver `www.google.com`. Envía un paquete con origen `192.168.1.10`.
2.  **Traducción (Salida):** El paquete llega al router. El router dice: *"Espera, no puedes salir con esa ropa de casa"*. Cambia la IP de origen `192.168.1.10` por su propia IP pública `203.0.113.50`.
3.  **Registro:** El router anota en su **Tabla NAT**: *"Lo que salga por el puerto X corresponde a la laptop"*.
4.  **Respuesta:** Google responde a `203.0.113.50`.
5.  **Traducción (Entrada):** El router recibe el paquete, mira su tabla, recuerda que esa conversación era para la laptop, cambia la IP destino a `192.168.1.10` y lo entrega.

<img width="737" height="416" alt="image" src="https://github.com/user-attachments/assets/203a5364-65b6-4050-8465-49be6bc1b0e9" />

-----

### 5\. Los 3 Sabores de NAT 🍦

No todos los NAT son iguales. Aquí están los tipos que debes conocer:

| Tipo | Descripción | Analogía |
| :--- | :--- | :--- |
| **Static NAT** | **Mapeo 1 a 1.** Una IP privada se vincula permanentemente a una IP pública específica. | Como tener un teléfono directo para el CEO. Nadie más lo usa. |
| **Dynamic NAT** | **Pool de direcciones.** Tienes un grupo de IPs públicas y se asignan a las privadas según se necesiten ("primero en llegar, primero en servirse"). | Como los casilleros de un gimnasio. Tomas cualquiera que esté libre. |
| **PAT (Port Address Translation)** | **Mapeo Muchos a 1.** También llamado **NAT Overload**. Múltiples IPs privadas usan UNA sola IP pública, diferenciándose por el **número de puerto**. | **Esta es la más común en casas.** Es como un edificio de apartamentos: misma dirección postal, diferente número de apartamento (puerto). |

<img width="741" height="446" alt="image" src="https://github.com/user-attachments/assets/90a71711-7c91-4294-b1be-77451951d64e" />


> **💡 Nota:** En tu casa usas **PAT**. Tu router usa puertos dinámicos (ej: puerto 4444 para tu móvil, puerto 5555 para tu PC) para saber a quién devolverle los datos de Google.

-----

### 6\. Beneficios y Sacrificios ⚖️

**✅ Lo Bueno (Beneficios):**

  * **Conservación:** Salva el espacio de direcciones IPv4.
  * **Seguridad:** Oculta la estructura interna de tu red. El mundo exterior solo ve al router, no a tus dispositivos individuales.
  * **Flexibilidad:** Puedes cambiar tu red interna sin tener que pedirle nada a tu ISP.

**❌ Lo Malo (Trade-Offs):**

  * **Complejidad:** Si quieres montar un servidor (como uno de Minecraft o Web) en tu casa, nadie puede entrar porque el router bloquea el tráfico no solicitado. Necesitas configurar **Port Forwarding**.
  * **Rompe Protocolos:** Algunas aplicaciones antiguas que necesitan conexión directa punto a punto odian el NAT.
  * **Troubleshooting:** Hace más difícil rastrear problemas de conectividad porque la IP cambia en el camino.

-----

### 7\. Aplicación Práctica: ¿Cómo veo el NAT en acción? 🛠️

Aunque no haremos un laboratorio paso a paso aquí, es importante que sepas cómo verificar esto en la vida real.

1.  **En tu computadora:** Abre una terminal o consola.
      * Ejecuta `ipconfig` (Windows) o `ip a` (Linux). Verás tu IP privada (ej: `192.168.1.15`).
2.  **En el navegador:** Ve a un sitio como "cual-es-mi-ip.net".
      * Verás una IP totalmente diferente (ej: `180.20.20.1`). Esa es la **IP Pública** de tu router.
3.  **La conclusión:** La diferencia entre esas dos IPs es la evidencia de que **NAT** está ocurriendo en tu router ahora mismo.

-----

### 🎓 Resumen para llevar

  * **IPv4 se agotó:** NAT es el parche que nos permite seguir creciendo usando direcciones privadas internamente.
  * **Públicas vs Privadas:** Las públicas viajan por internet; las privadas (RFC 1918) se quedan en casa.
  * **El Router es el Rey:** Actúa como intermediario modificando las cabeceras de los paquetes.
  * **PAT es el estándar:** En redes domésticas, usamos puertos para diferenciar el tráfico de muchos dispositivos usando una sola IP pública.

-----

### Comprobación de conocimientos 🧠
A ver si prestaste atención a los detalles técnicos. Intenta responder antes de abrir la solución.

1. ¿Qué tipo de NAT permite que múltiples direcciones IP privadas compartan una sola dirección IP pública utilizando números de puerto únicos?

<details> <summary><strong>Ver Respuesta</strong></summary>

Port Address Translation (PAT): También conocido como NAT Overload, es el estándar en redes domésticas para multiplexar conexiones.

</details>

2. ¿Qué RFC especifica los rangos de direcciones IP privadas?

<details> <summary><strong>Ver Respuesta</strong></summary>

RFC 1918: Este documento define los rangos 10.x.x.x, 172.16.x.x - 172.31.x.x, y 192.168.x.x.

</details>

3. ¿Qué tipo de NAT implica un mapeo uno a uno de direcciones IP privadas a direcciones IP públicas?

<details> <summary><strong>Ver Respuesta</strong></summary>

Static NAT: Se usa cuando necesitas que un dispositivo interno específico sea siempre accesible desde fuera con la misma IP pública.

</details>

4. ¿Qué tipo de NAT asigna una IP pública de un grupo (pool) según sea necesario?

<details> <summary><strong>Ver Respuesta</strong></summary>

Dynamic NAT: Asigna IPs temporalmente de un conjunto disponible. Si se acaban las IPs del pool, nuevos usuarios no pueden salir.

</details>

5. ¿Qué dispositivo realiza típicamente la función de NAT en una red doméstica?

<details> <summary><strong>Ver Respuesta</strong></summary>

El Router: Es el dispositivo de borde que conecta la red LAN (privada) con la WAN (pública/Internet).

</details>
