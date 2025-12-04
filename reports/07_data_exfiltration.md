# 🛡️ Reporte 07 — Data Exfiltration (Robo y extracción de datos)

## 🎯 Objetivo
Determinar si un atacante, después de comprometer una cuenta y moverse lateralmente, ha extraído información sensible fuera de la organización.

---

## 🧩 1. Datos del incidente

Máquina afectada: **WIN-FIN01**  
Usuario previamente comprometido: **Carlos.P**

Eventos relevantes:

| Hora     | Evento                                           |
|----------|--------------------------------------------------|
| 02:11 AM | ZIP creado con 243 archivos sensibles            |
| 02:13 AM | Conexión saliente a IP externa 185.77.92.11      |
| 02:13 AM | Subida de archivo ZIP de 1.6 GB                  |
| 02:14 AM | Conexión cerrada                                 |

---

## 🧠 2. Enriquecimiento de IP externa

**IP:** 185.77.92.11  
**Ubicación:** Europa del Este  
**Proveedor:** Hosting desconocido  
**Reputación:**  
- Reportes previos de malware  
- Asociada a campañas de exfiltración  

Interpretación:  
Alta probabilidad de actividad maliciosa.

---

## 🧠 3. Análisis humano (AI-proof)

- El usuario no trabaja en horarios nocturnos.  
- WIN-FIN01 no debe subir archivos a internet.  
- El tamaño (1.6 GB) es inusual.  
- El ZIP contiene información sensible (nómina y HR).  
- Ocurre después del movimiento lateral detectado.

Esto indica una **exfiltración deliberada**, no un error.

---

## 🚨 4. Conclusión

El atacante empaquetó grandes volúmenes de información sensible y los transfirió a un servidor externo malicioso.  
El incidente representa una **brecha de seguridad crítica**.

---

## 🛡️ 5. Acciones recomendadas

1. Aislar inmediatamente WIN-FIN01.  
2. Resetear credenciales del usuario afectado.  
3. Bloquear acceso a la IP atacante.  
4. Revisar si hubo otros envíos de datos.  
5. Correlacionar actividad en otros servidores.  

---

## 🧭 6. MITRE ATT&CK

- **T1560 – Archive Collected Data**  
- **T1041 – Exfiltration Over Command and Control Channel**  

---

## 📝 7. Resumen ejecutivo

Se confirma exfiltración de datos sensibles desde un servidor financiero hacia una IP maliciosa en Europa del Este.  
El incidente ocurrió tras compromiso de credenciales y movimiento lateral.  
Acción urgente requerida.

