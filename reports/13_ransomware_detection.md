# 🛡️ Reporte 13 — Ransomware Detection

## 🎯 Objetivo
Detectar comportamientos típicos de ransomware antes y durante la fase de cifrado, utilizando indicadores de archivos, procesos, red y comportamiento del sistema.

---

# 🧠 1. ¿Qué es ransomware?
Es un tipo de malware que:

1. Entra (phishing, credenciales robadas, vulnerabilidades).  
2. Se mueve dentro de la red.  
3. Cifra archivos del sistema.  
4. Exige un rescate para desbloquearlos.  

La detección temprana evita que afecte todo el negocio.

---

# 🟦 2. Indicadores clásicos de ransomware (antes del cifrado)

## 1️⃣ Actividad sospechosa en PowerShell
Ejemplo:
powershell.exe -nop -w hidden -enc ...
Los atacantes usan PowerShell para:
- descargar payloads  
- deshabilitar antivirus  
- ejecutar scripts  

---

## 2️⃣ Deshabilitar seguridad
Comandos frecuentes:
- Stop-Service WinDefend  
- Modificación de políticas de Windows  
- Cambios en antivirus/EDR  

---

## 3️⃣ Creación repentina de procesos desconocidos
Ejemplos:
- `encryptor.exe`  
- `locker.exe`  
- procesos con nombres aleatorios

---

# 🟥 3. Indicadores DURANTE el cifrado

## 1️⃣ Cambios masivos de archivos en segundos
Miles de archivos con nuevas extensiones:
- `.locked`  
- `.encrypted`  
- `.pay`  
- `.xyz`  

---

## 2️⃣ Alto uso de CPU y disco
Procesos como:
vssadmin.exe delete shadows
wmic.exe shadowcopy delete
Ransomware borra las copias de seguridad del sistema.

---

## 3️⃣ Notas de rescate
El SIEM detecta creación de archivos como:
READ_ME.txt
HOW_TO_DECRYPT.html
RECOVERY_INSTRUCTIONS.txt


---

# 🟩 4. Caso simulado (para el reporte)

Máquina afectada: **FIN-SRV03**

### Log de eventos:

| Hora        | Evento |
|-------------|--------|
| 01:14 AM | powershell.exe -nop -w hidden -enc ... |
| 01:15 AM | vssadmin.exe delete shadows /all |
| 01:15 AM | 3,200 archivos modificados en 45 segundos |
| 01:15 AM | nuevas extensiones: .encrypted |
| 01:16 AM | creación de archivo: READ_ME.html |
| 01:17 AM | proceso encryptor.exe consumiendo 92% CPU |

Interpretación inmediata:
- Se deshabilitaron sombras → clásico movimiento de ransomware.  
- Se observó cifrado masivo.  
- Se creó nota de rescate.  
- Proceso malicioso activo.

Esto es un ataque **confirmado** de ransomware.

---

# 🧠 5. Análisis (razonamiento humano — AI-proof)

- PowerShell oculto sugiere ejecución maliciosa.  
- `vssadmin` eliminando sombras indica preparación para cifrado.  
- El aumento repentino en archivos con extensión `.encrypted` confirma la fase activa del ataque.  
- La nota READ_ME.html es prueba de que la infección está operando.  
- El consumo de CPU por `encryptor.exe` indica cifrado en tiempo real.

Conclusión:
> “FIN-SRV03 está bajo ataque de ransomware en curso.”

---

# 🚨 6. Acciones de respuesta recomendadas (SOC Playbook)

1. **Aislar FIN-SRV03 inmediatamente.**  
2. Detener proceso `encryptor.exe`.  
3. Bloquear la IP o dominio de origen.  
4. Evitar que se propague a otros segmentos.  
5. Buscar movimiento lateral (otras máquinas afectadas).  
6. Revisar registros VSS, PowerShell y eventos recientes.  
7. Coordinar con incident response para restaurar backups.  
8. Activar procedimientos legales y de comunicación.

---

# 🧭 7. Mapeo MITRE ATT&CK
- **T1059 — Execution (PowerShell)**  
- **T1490 — Inhibit System Recovery**  
- **T1486 — Data Encrypted for Impact**  
- **T1489 — Service Stop**  
- **T1565 — Impact**  

---

# 📝 8. Resumen Ejecutivo
FIN-SRV03 está experimentando un ataque activo de ransomware.  
Los logs muestran ejecución maliciosa vía PowerShell, eliminación de sombras, cifrado masivo de archivos y creación de notas de rescate.  
Requiere respuesta inmediata para contener el ataque y mitigar impacto.

