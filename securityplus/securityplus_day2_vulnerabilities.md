# 🔐 Security+ — Día 2  
# Vulnerabilidades, Exposición, Amenazas y Riesgo (Nivel A)

---

## 🧠 1. ¿Qué es una vulnerabilidad? (explicado muy simple)

**Una vulnerabilidad es una debilidad.**  
Algo que “no está bien protegido”.

Ejemplos simples:
- Una ventana sin seguro → vulnerabilidad  
- Una contraseña débil → vulnerabilidad  
- Un software sin actualizar → vulnerabilidad  

En tecnología:
- un puerto abierto innecesario  
- un sistema sin parches  
- una contraseña “123456”  

SOC connection:  
Detectamos cuando alguien intenta **aprovechar esa debilidad**.

---

## 🧠 2. ¿Qué es una amenaza?

Una *amenaza* es **algo que podría causar daño**.

Ejemplos:
- un hacker  
- un malware  
- un correo de phishing  
- un USB infectado  

La amenaza no siempre causa daño.  
Es *la posibilidad*.

---

## 🧠 3. ¿Qué es un exploit?

Un exploit es **usar la vulnerabilidad**.

Ejemplo muy simple:
- Ventana mal cerrada (vulnerabilidad)  
- Ladrón entra por ahí (exploit)

En informática:
- Software viejo → atacante usa un exploit para entrar  
- Contraseña débil → fuerza bruta la adivina  

---

## 🧠 4. ¿Qué es el riesgo?

Riesgo =  
**vulnerabilidad + amenaza**

Ejemplo:
- Hay una ventana abierta (vulnerabilidad)  
- Hay ladrones en el barrio (amenaza)  
→ Hay riesgo de robo.

En Security+ lo verás así:
> Riesgo = probabilidad + impacto

---

## 🧠 5. ¿Qué es “exposición”?

Exposición es **cuánto estás expuesto a un riesgo**.

Ejemplos:
- Tu contraseña filtrada → alta exposición  
- Puerto de administración abierto al internet → alta exposición  
- Servidor detrás de firewall → baja exposición  

---

# 🔧 6. Ejemplos del mundo real para entenderlo sin memorizar

### 🔹 Vulnerabilidad  
Tu iPhone está desactualizado.

### 🔹 Amenaza  
Un atacante encuentra un fallo en esa versión.

### 🔹 Exploit  
El atacante usa ese fallo para entrar.

### 🔹 Riesgo  
Podrían robar tus fotos, contactos, etc.

### 🔹 Exposición  
No tienes MFA ni código → exposición alta.

---

# 🛡️ 7. ¿Cómo lo ve un SOC Analyst?

Mucho más simple de lo que suena:

- Una máquina no actualizada → vulnerabilidad  
- Un ataque que llega → amenaza  
- Un intento de exploit → alerta en el SIEM  
- Un éxito de exploit → incidente  
- Exposición → máquinas que no están protegidas igual  

En tus reportes anteriores viste ejemplos de:
- phishing (amenaza)  
- credenciales robadas (vulnerabilidad humana)  
- lateral movement (exploit interno)  
- riesgo crítico (servidor financiero)  

---

# 📝 8. MINI-PRÁCTICA (estilo Security+)

❓ **1. Tener una contraseña muy débil es:**  
A) Amenaza  
B) Vulnerabilidad  
C) Riesgo  

**Respuesta:** B (debilidad)

---

❓ **2. Phishing es:**  
A) Amenaza  
B) Vulnerabilidad  
C) Exposición  

**Respuesta:** A (un ataque que podría ocurrir)

---

❓ **3. Si un atacante aprovecha un fallo en Windows para entrar, eso se llama:**  
A) Exploit  
B) Riesgo  
C) Exposición  

**Respuesta:** A

---

# ⭐ 9. Resumen final para memorizar

- **Vulnerabilidad** = debilidad  
- **Amenaza** = algo que puede causar daño  
- **Exploit** = usar la vulnerabilidad para atacar  
- **Riesgo** = vulnerabilidad + amenaza  
- **Exposición** = qué tan accesible o desprotegido estás  

Listo. Nada que memorizar, todo lógico.

