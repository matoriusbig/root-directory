# 08 - Arquitectura de Internet 🏗️

> **🎯 Objetivo:** Dejar de ver Internet como una "nube mágica" y entender los planos reales de cómo se conectan las cosas. Aprenderás por qué Netflix no usa la misma estructura que BitTorrent y cómo elegimos el diseño perfecto según el problema a resolver.

-----

### 1\. ¿Qué es la Arquitectura de Internet? 📐

Imagina que eres un arquitecto de edificios. No diseñarías un rascacielos igual que una casa de campo, ¿verdad? En redes pasa lo mismo.

La **Arquitectura de Internet** define cómo se organizan, transmiten y gestionan los datos. No hay una "talla única"; cada modelo tiene sus ventajas (superpoderes) y desventajas (kriptonita) en términos de escalabilidad, seguridad y costo.

-----

### 2\. Peer-to-Peer (P2P): Todos para Uno y Uno para Todos 🤝

En una red **P2P (Peer-to-Peer)**, eliminamos al intermediario. Aquí, cada dispositivo (nodo) es **cliente y servidor** al mismo tiempo. Es la democracia digital pura.

> **💡 La Analogía de las Fotos:** 📸
> Imagina un grupo de amigos que quiere compartir fotos de vacaciones.
>
>   * **Método tradicional:** Todos suben las fotos a Google Drive (Servidor Central).
>   * **Método P2P:** Cada amigo abre una carpeta en su PC y conecta un cable directo a los demás. Juan descarga las fotos directamente del disco duro de María. No hay "nube" central.

**Ejemplo Clásico:** Torrenting (BitTorrent).

  * **Seeder:** Alguien que tiene el archivo completo y lo comparte.
  * **Leecher:** Alguien que está descargando pedazos de muchos seeders a la vez.

<img width="987" height="691" alt="image" src="https://github.com/user-attachments/assets/cf009f80-af53-4a10-801e-acbcf579b07f" />


#### ⚖️ Balance del P2P

| Ventaja (Luz ☀️) | Descripción |
| :--- | :--- |
| **Escalabilidad** | Cuanta más gente se une, más rápida y potente se vuelve la red (más recursos). |
| **Resiliencia** | Si un nodo se cae, la red sigue viva. No hay un "jefe" que matar. |
| **Costo** | Barato. Usas el ancho de banda y disco duro de los usuarios, no el tuyo. |

| Desventaja (Sombra 🌑) | Descripción |
| :--- | :--- |
| **Gestión Caótica** | Es una pesadilla controlar actualizaciones o políticas de seguridad. |
| **Seguridad** | Cada nodo está expuesto. Estás abriendo tu puerta a extraños. |

-----

### 3\. Client-Server: El Modelo Rey 👑

Este es el estándar de la industria (Websites, Email, Apps bancarias). Es una jerarquía estricta.

  * **Cliente:** El que pide (tu navegador, tu celular).
  * **Servidor:** El que tiene los datos y responde (una máquina potente en un datacenter).

> **El Restaurante:** 🍽️
> Tú eres el cliente. El servidor es la cocina.
> Tú pides el menú (Request), la cocina prepara el plato y te lo entrega (Response). Tú no entras a cocinar, y la cocina no se sienta a comer. Roles separados.

<img width="990" height="527" alt="image" src="https://github.com/user-attachments/assets/e14674cc-6201-4475-b3f0-ff43662d1ad6" />


#### 🍰 El Modelo de Capas (Tiers)

Para organizar mejor el caos, dividimos al servidor en capas lógicas:

1.  **Single-Tier (Todo en uno):** Base de datos, lógica e interfaz en UNA máquina. *Peligroso y poco escalable.*
2.  **Two-Tier (Escritorio clásico):** Cliente (interfaz) habla directo con la Base de Datos.
      * > **💡 Nota:** Navegar por la web **NO** es Two-Tier normalmente, porque el navegador habla con un Web Server, no con la Base de Datos directamente.
3.  **Three-Tier (El estándar Web):**
      * **Capa 1 (Cliente):** Lo que ves (Presentación).
      * **Capa 2 (App Server):** El cerebro. Procesa la lógica ("¿Tiene saldo esta cuenta?").
      * **Capa 3 (Database):** La caja fuerte. Guarda los datos crudos.
4.  **N-Tier:** Cuando el sistema es tan grande que dividimos la lógica en múltiples servidores especializados.

#### ⚖️ Balance Client-Server

| Ventaja ✅ | Desventaja ❌ |
| :--- | :--- |
| **Control Central:** Fácil de actualizar y proteger. | **Punto Único de Fallo:** Si el servidor cae, todos lloran. |
| **Seguridad:** Políticas estrictas en un solo lugar. | **Caro:** Mantener datacenters cuesta una fortuna. |
| **Optimización:** Servidores dedicados potentes. | **Congestión:** Si todos entran a la vez, se satura. |

-----

### 4\. Hybrid Architecture: Lo Mejor de Dos Mundos 🧬

¿Por qué elegir si puedes tener ambos? El modelo **Híbrido** usa un servidor central para coordinar, pero deja que los usuarios se pasen los datos pesados entre ellos.

> **El Ejemplo de Zoom/Skype:** 📹
>
>   * **Fase Servidor:** Cuando te logueas, un servidor central verifica tu contraseña y te dice quién está conectado.
>   * **Fase P2P:** Cuando empieza la videollamada, el video viaja (idealmente) directo de mi cámara a tu pantalla.
>
> **Resultado:** Menos carga para el servidor, menos lag para los usuarios.

-----

### 5\. Cloud Architecture: La Computadora de Otro ☁️

La "Nube" es solo un nombre elegante para "usar los servidores de Amazon/Google/Microsoft a través de Internet".

**Características Vitales:**

1.  **Autoservicio:** Te sirves tú mismo sin llamar a soporte.
2.  **Acceso Universal:** Desde cualquier dispositivo con internet.
3.  **Elasticidad:** ¿Necesitas 100 servidores por una hora? Click. ¿Ya no los necesitas? Click.
4.  **Pago por uso:** Como la luz o el agua. Pagas lo que consumes.

<!-- end list -->

  * **Ventaja:** No compras hardware, escalabilidad infinita.
  * **Riesgo:** "Vendor Lock-in" (casarse con un proveedor y que sea difícil divorciarse) y privacidad de datos.

-----

### 6\. Software-Defined Networking (SDN): El Cerebro Separado 🧠

Tradicionalmente, los routers eran cajas tontas que tenían que configurarse una por una. **SDN** cambia el juego separando el cerebro del músculo.

  * **Control Plane (Cerebro):** Decide por dónde van los datos. En SDN, esto es **Software centralizado**.
  * **Data Plane (Músculo):** Los dispositivos que mueven los paquetes. Solo obedecen órdenes.

> **La Magia:** Permite a los administradores reprogramar toda la red desde una consola central en segundos, en lugar de tocar 500 routers manualmente. Es vital para grandes empresas y nubes.

-----

### 🎓 Resumen para llevar

  * **P2P:** Democracia total. Escalable y resiliente, pero difícil de controlar (Ej: Torrents).
  * **Client-Server:** Jerarquía estricta. Fácil de controlar, pero caro y con punto único de fallo (Ej: Webs).
  * **3-Tier:** La forma profesional de hacer Client-Server (Presentación -\> Lógica -\> Datos).
  * **Híbrido:** Servidor para el login, P2P para la data pesada (Ej: Videochats).
  * **SDN:** Separa el cerebro (Control) del músculo (Data) para programar la red.

-----
### Comprobación de conocimientos 🧠
¡Hora de poner a prueba tu arquitectura mental!

1. ¿Qué tipo de arquitectura permite que los nodos actúen tanto como cliente y servidor?

<details> <summary><strong>Ver Respuesta</strong></summary>

Peer-to-Peer (P2P): En este modelo, todos los pares son iguales y comparten recursos directamente.

</details>

2. ¿Qué arquitectura combina elementos de los modelos Cliente-Servidor y Peer-to-Peer?

<details> <summary><strong>Ver Respuesta</strong></summary>

Hybrid Architecture: Utiliza servidores centrales para la coordinación y conexiones directas para la transferencia de datos.

</details>

3. ¿Qué modelo de servicio en la nube implica acceder a aplicaciones a través de Internet sin gestionar la infraestructura subyacente?

<details> <summary><strong>Ver Respuesta</strong></summary>

SaaS (Software as a Service): Ejemplos como Google Drive o Dropbox donde solo usas el software final.

</details>

4. ¿En qué arquitectura se separa el plano de control del plano de datos?

<details> <summary><strong>Ver Respuesta</strong></summary>

Software-Defined Networking (SDN): Permite la gestión centralizada y programable de la red.

</details>

5. ¿Qué arquitectura es conocida por el intercambio de datos descentralizado sin un servidor central?

<details> <summary><strong>Ver Respuesta</strong></summary>

Peer-to-Peer (P2P): Ideal para compartir archivos sin depender de una entidad central.

</details>

6. ¿Qué modelo utilizan las aplicaciones de videoconferencia para combinar la coordinación centralizada con la transferencia de datos peer-to-peer?

<details> <summary><strong>Ver Respuesta</strong></summary>

Hybrid Architecture: Garantiza un inicio de sesión seguro (centralizado) y una transmisión de video rápida (P2P).

</details>
