# 🔐 Security+ — Día 21  
# Wireless Security, WPA3, Authentication & Hardening

## 🎯 Objetivo
Dominar las tecnologías, protocolos de seguridad, modos de autenticación y ataques comunes en redes inalámbricas. Este tema es muy frecuente en Security+ y crucial en la vida real.

---

# 🟥 1. Estándares Wi-Fi (IEEE 802.11)

## Bandas:
- 2.4 GHz → más alcance, menos velocidad  
- 5 GHz → más velocidad, menos alcance  
- 6 GHz (Wi-Fi 6E) → moderno, menor interferencia  

---

# 🟧 2. Modos de Seguridad Wi-Fi (muy preguntado)

## 🔴 WEP — Inseguro
- No se usa  
- Fácilmente crackeado  
- Nunca elegirlo  

## 🟠 WPA — Obsoleto  
- Mejor que WEP, pero inseguro hoy  

## 🟡 WPA2 — Estándar durante muchos años  
- Aún común  
- Basado en AES-CCMP  
- Todavía seguro si se configura bien  

## 🟢 WPA3 — Estándar moderno (lo mejor actualmente)
- Mucho más seguro  
- No vulnerable a diccionarios offline  
- Usa SAE (Simultaneous Authentication of Equals)  

WPA3 = respuesta correcta casi siempre en Security+ cuando preguntan "¿cuál es el nivel más alto de seguridad?"

---

# 🟩 3. WPA2 vs WPA3

| Característica | WPA2 | WPA3 |
|----------------|------|-------|
| Cifrado | AES-CCMP | SAE + GCMP |
| Protección contra ataque de diccionario | ❌ | ✔ |
| Perfect Forward Secrecy | ❌ | ✔ (SAE) |
| Seguridad general | Alta | **Muy alta** |
| Recomendado en 2025 | Sólo si no hay opción | **Sí** |

---

# 🟦 4. Métodos de Autenticación Wi-Fi

## 🔸 WPA2/WPA3-PSK (Personal)
- Contraseña compartida  
- Hogares o pequeñas oficinas  
- Riesgo: misma clave para todos  

## 🔸 WPA2/WPA3-Enterprise (EAP)
Usa **802.1X + RADIUS**  
- Autenticación individual para cada usuario  
- Certificados o credenciales únicas  
- Mucho más seguro  
- Usado en empresas, universidades, hospitales  

Tipos de EAP:
- EAP-TLS (más seguro, usa certificados)  
- PEAP (común y seguro)  
- EAP-TTLS  

**Si la pregunta dice “lo más seguro para empresas” → EAP-TLS.**

---

# 🟫 5. Ataques comunes a Wi-Fi

## 🔸 Evil Twin
Un atacante crea un Wi-Fi falso con mismo nombre (SSID).  
Objetivo:
- robar credenciales  
- interceptar tráfico  

Contramedida:
- WPA3  
- certificados  
- evitar redes públicas  

---

## 🔸 Deauthentication Attack
Se expulsa al usuario de su red → fuerza reconexión → captura de handshake.

Contramedida:
- WPA3  
- Management Frame Protection  

---

## 🔸 War Driving
Conducir mientras se escanean redes Wi-Fi vulnerables.

---

## 🔸 Rogue AP (Punto de acceso no autorizado)
Un empleado o atacante conecta su propio router → crea vector de ataque interno.

SOC debe detectar:
- nuevos BSSIDs  
- tráfico inusual  
- dispositivos no aprobados  

---

# 🟪 6. Hardening de Wi-Fi (configuración segura)

✔ Cambiar SSID por defecto  
✔ WPA3 si es posible  
✔ Contraseña larga y fuerte  
✔ Filtrar dispositivos por certificados (en Enterprise)  
✔ Deshabilitar WPS  
✔ Usar VLANs para invitados  
✔ Separar red IoT  
✔ Habilitar Management Frame Protection  

---

# 🟨 7. Seguridad en redes públicas (SOC lo ve diario)

Peligros:
- MITM  
- Evil Twin  
- Captura de tráfico sin cifrar  
- Robo de tokens de sesión  

Buenas prácticas:
- No login sensibles  
- Usar VPN  
- Preferir datos móviles  

---

# 🧭 8. Qué ve un SOC sobre Wi-Fi

- conexiones desde SSID desconocidos  
- implementaciones mal configuradas  
- nuevos AP detectados  
- fallas masivas de autenticación (ataque de diccionario)  
- desconexiones repetidas (ataque deauth)  
- actividad sospechosa en guest networks  

---

# 📝 9. Mini-Práctica (Security+ Style)

**1. ¿Cuál es el estándar Wi-Fi más seguro hoy?**  
➡️ WPA3

**2. ¿Qué protocolo usa autenticación basada en certificados?**  
➡️ EAP-TLS

**3. ¿Qué ataque crea un AP falso?**  
➡️ Evil Twin

**4. ¿Qué deshabilitar para evitar accesos fáciles?**  
➡️ WPS

**5. ¿Qué modo es más seguro para empresas?**  
➡️ WPA3-Enterprise (802.1X + RADIUS)

---

# ⭐ Resumen Final
- WPA3 = lo más seguro hoy  
- EAP-TLS = autenticación más fuerte  
- Enterprise mode = para empresas  
- Ataques frecuentes: Evil Twin, deauth, rogue AP  
- Hardening es clave para SOC y para Security+  
