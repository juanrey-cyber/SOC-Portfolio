# 🛡️ Reporte 04 — Phishing con Robo de Credenciales (Credential Theft)

## 🎯 Objetivo
Identificar y documentar un incidente donde un usuario cae en un ataque de phishing, sus credenciales son robadas y posteriormente utilizadas por un atacante para acceder al sistema desde un país no habitual.

---

## 📬 1. Descripción del Incidente

El usuario **Juan.R** recibió un correo falso simulando ser de Microsoft.  
Tras hacer clic en el enlace, fue redirigido a una página de login falsificada donde ingresó sus credenciales reales.

Minutos después, dichas credenciales fueron utilizadas por un atacante para iniciar sesión desde una ubicación geográfica no asociada al usuario.

---

## 🕒 2. Línea de Tiempo

| Hora  | Evento |
|-------|--------|
| 09:14 | Usuario recibe correo phishing |
| 09:15 | Usuario introduce su contraseña en sitio falso |
| 09:18 | Login exitoso desde IP atacante: 102.133.45.22 |
| 09:19 | Segundo login desde misma IP |
| 09:22 | Atacante revisa inbox |
| 09:24 | Atacante intenta crear regla de reenvío (acto malicioso) |

---

## 🌍 3. Enriquecimiento de la IP Atacante

**IP:** 102.133.45.22  
**País:** Nigeria  
**Proveedor:** MTN Mobile (móvil)  
**Reputación:**  
- Reportada por campañas de phishing previas  
- Actividad fraudulenta en múltiples plataformas  

**Interpretación:**  
Alta probabilidad de uso por delincuentes; coincide con comportamientos de robo de credenciales.

---

## 🧠 4. Análisis Humano (AI-Proof)

- El usuario no viaja → login desde Nigeria imposible.  
- El login ocurrió minutos después de que el usuario colocó su contraseña en un enlace falso → causalidad directa.  
- Proveedor móvil sugiere atacante dinámico, no corporativo.  
- La creación de reglas de reenvío es una técnica común de robo de información.  

**Conclusión:**  
Compromiso completo de la cuenta.

---

## 🚨 5. Conclusión

El incidente corresponde a un ataque de **phishing con robo de credenciales**, seguido de acceso no autorizado.  
El atacante utilizó credenciales válidas, lo cual evita detección basada en fallos de login.

---

## 🛡️ 6. Acciones de Contención

1. Resetear contraseña inmediatamente.  
2. Cerrar todas las sesiones activas.  
3. Reforzar MFA.  
4. Bloquear IP atacante.  
5. Revisar reglas de reenvío y eliminar las maliciosas.  

---

## 🔧 7. Recomendaciones

- Entrenamiento de phishing al usuario.  
- Monitoreo de actividad inusual por geolocalización.  
- Alertas de “impossible travel”.  
- Revisión de logs de actividad posterior.  

---

