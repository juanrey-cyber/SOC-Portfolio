# 🛡️ Reporte 02 — Análisis de Timing en Intentos de Login (Brute Force)

## 🎯 Objetivo
Identificar patrones de ataque de fuerza bruta mediante el análisis del intervalo entre intentos fallidos de autenticación. Distinguir entre error humano normal y actividad automatizada maliciosa.

---

## 📊 Datos Analizados
| Timestamp  | IP            | Usuario | Resultado |
|------------|--------------|---------|-----------|
| 10:01:01   | 203.0.113.10 | admin   | FAIL      |
| 10:01:17   | 203.0.113.10 | admin   | FAIL      |
| 10:01:32   | 203.0.113.10 | admin   | FAIL      |
| 10:01:46   | 203.0.113.10 | admin   | FAIL      |
| 10:01:57   | 203.0.113.10 | admin   | FAIL      |

---

## 🧠 Observaciones
- Todos los intentos provienen de la **misma IP externa**.
- Todos los eventos ocurren dentro de un intervalo **menor a 1 minuto**.
- Los intentos tienen un patrón aproximado de **cada 15 segundos**.
- El usuario atacado es **“admin”**, una cuenta de alto valor.
- El patrón es **demasiado consistente** para ser un error humano.

---

## 🧠 Análisis Humano (AI-Proof)
El comportamiento repetitivo en intervalos regulares indica automatización.  
Un humano cometería errores de forma más dispersa, con tiempos irregulares y variaciones mayores.

Esto sugiere:
- Script automatizado  
- Posible herramienta de fuerza bruta  
- Intento de validación de credenciales  
- Ataque dirigido a cuenta privilegiada  

---

## 🚨 Conclusión
El evento corresponde a un **posible ataque de fuerza bruta automatizado**.  
La consistencia en el timing, la IP repetida y el objetivo “admin” indican actividad maliciosa.

---

## 🛡️ Recomendaciones SOC
1. **Bloquear temporalmente la IP 203.0.113.10.**
2. **Revisar intentos de login posteriores** por si hubo éxito.
3. Configurar **rate limiting** en el servicio.
4. Habilitar o reforzar **MFA** en cuentas privilegiadas.
5. Revisar logs del firewall relacionados con esa IP.

