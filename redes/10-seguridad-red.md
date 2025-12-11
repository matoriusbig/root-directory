# 10 - Fundamentos de Seguridad de Red: Tu Escudo Digital 🌐

> **🎯 Objetivo:** Comprenderás los pilares fundamentales que mantienen una red segura y dominarás las herramientas defensivas críticas (Firewalls e IDS/IPS) para proteger la información contra accesos no autorizados. ¡Es hora de blindar el sistema\!

-----

## 1\. La Santísima Trinidad de la Seguridad: La Tríada CIA 🔺

En el mundo de las redes, la "seguridad" no es un concepto abstracto. Es un conjunto de medidas tangibles para proteger datos y sistemas. Todo lo que hacemos gira en torno a mantener intacta la **Tríada CIA** (Confidencialidad, Integridad y Disponibilidad).

Imagina que tu red es una bóveda de banco de alta seguridad. La Tríada CIA son las reglas que rigen esa bóveda:

| Principio | Concepto en Inglés | Descripción |
| :--- | :--- | :--- |
| **Confidencialidad** 🤫 | Confidentiality | Solo las personas con permiso (autorizadas) pueden ver lo que hay dentro. |
| **Integridad** ✍️ | Integrity | Los datos no han sido alterados ni manipulados por nadie. Lo que guardaste es exactamente lo que recuperas. |
| **Disponibilidad** ⏱️ | Availability | Los recursos están ahí cuando los necesitas. Si la red se cae, la seguridad falla. |

-----

## 2\. Firewalls: Los Porteros de la Red 🧱

Un **Firewall** (Cortafuegos) es tu primera línea de defensa. Puede ser hardware (una caja física), software (un programa) o ambos.

> **🏢 La Analogía del Portero:**
> Imagina un **guardia de seguridad** en la entrada de un edificio corporativo muy estricto. Este guardia tiene una lista de invitados (**Firewall Policies** o **ACLs**).
>
>   * Si tu nombre está en la lista: **Pases (Allow).**
>   * Si no estás en la lista: **Te quedas fuera (Block/Deny).**

Los firewalls miran los paquetes de datos y deciden su destino basándose en reglas predefinidas (IPs, Puertos, Protocolos). Además, registran (log) todo lo que pasa.


### Los 4 Tipos de Firewalls (Evolución) 🧬

No todos los guardias son iguales. Aquí tienes la evolución de su inteligencia:

#### 1\. Packet Filtering Firewall (Filtrado de Paquetes) 📨

  * **Nivel:** Capas 3 (Red) y 4 (Transporte) del modelo OSI.
  * **Cómo funciona:** Es el guardia básico. Solo mira tu "DNI": IP de origen, IP de destino y Puerto.
  * **Ejemplo:** Un router que dice "Solo acepto tráfico al puerto 80 (HTTP) y 443 (HTTPS), el resto se bloquea".

#### 2\. Stateful Inspection Firewall (Inspección de Estado) 🧠

  * **Nivel:** Más inteligente que el anterior.
  * **La Magia:** Rastrea el *estado* de la conexión. Recuerda la conversación.
  * **Ejemplo:** Si tú enviaste una solicitud a Google, este firewall recordará que tú iniciaste la charla y permitirá que la respuesta de Google entre. Si Google intenta hablarte sin que tú lo hayas llamado, bloqueará la entrada.

#### 3\. Application Layer Firewall (Proxy) 🕵️

  * **Nivel:** Capa 7 (Aplicación).
  * **Cómo funciona:** Este guardia no solo mira tu DNI, **abre tu mochila**. Inspecciona el contenido real del tráfico.
  * **Ejemplo:** Puede bloquear una solicitud HTTP maliciosa incluso si el puerto 80 está abierto, porque ve patrones raros dentro del paquete.

#### 4\. Next-Generation Firewall (NGFW) 🤖

  * **Nivel:** El "Robocop" de los firewalls.
  * **Cómo funciona:** Combina la memoria del *Stateful Inspection* con características avanzadas como inspección profunda de paquetes (DPI), antivirus integrado y control de aplicaciones.
  * **Ejemplo:** Un dispositivo moderno que bloquea IPs maliciosas conocidas globalmente y descifra tráfico encriptado para buscar virus.

<img width="865" height="857" alt="Firewall-1" src="https://github.com/user-attachments/assets/dbbf54b1-627e-41b6-91aa-2f9db3cc6046" />


> **💡 Nota:** En tu casa, el router probablemente tiene un firewall de software integrado. En una empresa grande, el firewall es un dispositivo físico dedicado que se coloca justo después del módem y antes de la red interna.

-----

## 3\. IDS e IPS: Los Vigilantes Activos 🚨

A veces, el guardia de la puerta (Firewall) deja pasar a alguien que parecía legítimo, pero que empieza a comportarse mal dentro del edificio. Aquí entran los sistemas de detección y prevención.

### La Gran Diferencia: IDS vs. IPS ⚔️

| Característica | **IDS** (Intrusion Detection System) | **IPS** (Intrusion Prevention System) |
| :--- | :--- | :--- |
| **Acción** | Detecta y **Alerta**. | Detecta y **Bloquea/Previene**. |
| **Analogía** | Una **alarma** antirrobo que suena y avisa a la policía, pero no detiene al ladrón. | Un sistema que detecta al ladrón y automáticamente **cierra las puertas** y suelta a los perros. |
| **Resultado** | El administrador recibe un aviso para investigar. | El tráfico malicioso es rechazado en tiempo real. |

<img width="789" height="851" alt="IPS_IDS-1" src="https://github.com/user-attachments/assets/46bd5b1a-fccf-48bc-8e93-ef006d0d2e4d" />

### ¿Cómo detectan a los malos? 🕵️‍♂️

Tanto IDS como IPS usan dos métodos principales:

1.  **Basado en Firmas (Signature-based):** Compara el tráfico con una base de datos de "delincuentes conocidos" (exploits ya descubiertos). Es como tener carteles de "Se Busca".
2.  **Basado en Anomalías (Anomaly-based):** Conoce lo que es "normal" en tu red. Si algo se sale de lo normal (ej: un usuario transfiriendo 500GB a las 3 AM), salta la alarma.

### Tipos de Implementación (¿Dónde viven?) 📍

  * **NIDS/NIPS (Network-based):** Se colocan en puntos estratégicos de la red (como el switch central) para ver **todo** el tráfico que pasa.
  * **HIDS/HIPS (Host-based):** Viven dentro de un dispositivo específico (tu servidor o laptop). Monitorean los archivos y logs de **esa** máquina en particular.

> **🛡️ Nota de Seguridad:** Una configuración común y segura es colocar el IDS/IPS **detrás** del Firewall. El Firewall filtra el "ruido" obvio, y el IDS/IPS analiza el tráfico restante con mayor profundidad. También se suelen poner en la **DMZ** (Zona Desmilitarizada) para proteger servidores expuestos a internet.

-----

## 4\. Mejores Prácticas: La Estrategia de Defensa 🏰

No basta con comprar los aparatos, hay que saber usarlos. Aquí están las reglas de oro para endurecer tu seguridad:

1.  **Políticas Claras:** Define reglas consistentes.
2.  **Principio de Mínimo Privilegio (Least Privilege):** Solo permite lo estrictamente necesario. Si un empleado no necesita acceder al servidor de pagos, bloquéalo.
3.  **Actualizaciones Regulares:** Mantén las firmas de tu IDS/IPS y el SO de tu Firewall al día. Las amenazas cambian a diario.
4.  **Monitoreo y Logs:** Revisa los registros. De nada sirve una alerta si nadie la lee.
5.  **Seguridad por Capas (Defense in Depth):** Esta es clave. No confíes en una sola herramienta. Usa Firewall + IDS + Antivirus + Educación al usuario. Si una capa falla, la siguiente detiene el ataque.
6.  **Penetration Testing (Pentesting):** Hackea tu propia red (o contrata a alguien) para probar si tus defensas realmente funcionan.

-----

## 5\. Explicación Práctica: Configuración de Reglas (Sin Laboratorio) 🛠️

En los cursos técnicos, a menudo usarás herramientas como **pfSense** (Firewall/Router Open Source) o **Suricata** (IDS/IPS). Aunque no haremos el laboratorio paso a paso aquí, es vital entender la lógica de configuración:

**El Escenario:** Imagina que eres el administrador y quieres bloquear todo el tráfico, excepto el acceso a tu servidor web.

1.  **En el Firewall (pfSense):**

      * Irías a la sección de "Rules" (Reglas).
      * Crearías una regla de "Block All" (Bloquear todo) al final de la lista.
      * Crearías una regla "Pass" (Permitir) arriba del todo especificando:
          * *Source:* Any (Cualquiera).
          * *Destination:* IP de tu servidor Web.
          * *Port:* 80/443 (HTTP/HTTPS).
      * *Resultado:* El firewall lee de arriba a abajo. Si es tráfico web, pasa. Si es cualquier otra cosa, llega al final y se bloquea.

2.  **En el IDS/IPS (Suricata):**

      * Habilitas el "Modo IPS" (Inline).
      * Cargas un conjunto de reglas (como las de Emerging Threats).
      * Si Suricata ve un paquete que coincide con la firma de un ataque conocido (ej: "Intento de SQL Injection"), automáticamente cortará la conexión y registrará el evento.

-----

### 🎓 Resumen para llevar

  * La **Tríada CIA** (Confidencialidad, Integridad, Disponibilidad) es el santo grial de la seguridad.
  * Los **Firewalls** filtran tráfico basándose en reglas; pueden ser simples (Packet Filtering) o muy avanzados (NGFW).
  * **IDS** detecta y avisa; **IPS** detecta y bloquea.
  * **Suricata** es una herramienta poderosa que puede actuar como ambos.
  * La estrategia de **Defensa en Profundidad** (capas) es superior a depender de un solo dispositivo.

-----

### Comprobación de conocimientos 🧠

Responde las siguientes preguntas para validar lo aprendido. ¡Piensa antes de mirar la respuesta\!

1. ¿Qué dispositivo monitorea el tráfico de red y aplica reglas para permitir o bloquear tráfico específico?

<details> <summary><strong>Ver Respuesta</strong></summary>

Firewall

Es el "portero" encargado de aplicar las políticas de control de acceso.

</details>

2. ¿Qué tipo de firewall opera en las capas de red y transporte del modelo OSI? (Formato: dos palabras)

<details> <summary><strong>Ver Respuesta</strong></summary>

Packet Filtering (o Filtrado de Paquetes)

Este tipo básico examina direcciones IP y puertos (Capas 3 y 4).

</details>

3. ¿Qué característica avanzada incluye un Firewall de Próxima Generación (NGFW) más allá de la inspección de estado? (Formato: tres palabras, en inglés como se usa en la industria)

<details> <summary><strong>Ver Respuesta</strong></summary>

Deep Packet Inspection (Inspección Profunda de Paquetes)

Permite al firewall mirar dentro del contenido de los paquetes, no solo en los encabezados.

</details>

4. ¿Qué sistema genera alertas sobre actividad de red sospechosa SIN bloquearla? (Formato: acrónimo)

<details> <summary><strong>Ver Respuesta</strong></summary>

IDS (Intrusion Detection System)

Recuerda: Detection = Detectar (solo avisa).

</details>

5. ¿Qué sistema no solo detecta sino que también previene la actividad sospechosa bloqueándola? (Formato: acrónimo)

<details> <summary><strong>Ver Respuesta</strong></summary>

IPS (Intrusion Prevention System)

Recuerda: Prevention = Prevenir (actúa y bloquea).

</details>

6. ¿Qué método de detección implica comparar el tráfico de red contra una base de datos de exploits conocidos? (Formato: tres palabras, en inglés o español técnico)

<details> <summary><strong>Ver Respuesta</strong></summary>

Signature-based detection (Detección basada en firmas)

Busca huellas digitales exactas de ataques conocidos previamente.

</details>

