# 🔐 Security+ — Día 33  
# Scripting Basics — PowerShell, Bash, Python & Regex (explicado fácil)

## 🎯 Objetivo
Aprender los fundamentos de scripting para seguridad: PowerShell, Bash, Python básico y Regex.  
Esto permite automatizar tareas, analizar logs y detectar actividad sospechosa.  
Es esencial para Security+, SOC II, Threat Hunting y DFIR Jr.

---

# 🟥 1. ¿Por qué usar scripts en ciberseguridad?

Un script permite:
- analizar miles de logs en segundos  
- automatizar tareas repetitivas  
- buscar patrones maliciosos  
- extraer información de sistemas  
- detectar anomalías  
- reducir trabajo manual  

La IA puede generar el script por ti,  
pero tú debes entender:
- qué hace el script  
- qué buscas  
- qué es anómalo  

---

# 🟧 2. PowerShell — explicado fácil (Windows)

PowerShell es el lenguaje de administración y automatización de Windows.

Ejemplos de comandos básicos:

    Get-Process
    Get-Service
    Get-EventLog -LogName Security
    Get-ChildItem

Uso en seguridad:
- ver procesos sospechosos  
- revisar servicios maliciosos  
- analizar eventos de seguridad  
- buscar archivos modificados  
- ver conexiones de red  
- enumerar usuarios y permisos  

Ejemplo útil (hunting de procesos que usan mucha CPU):

    Get-Process | Sort-Object CPU -Descending

---

# 🟨 3. Bash — explicado fácil (Linux / Mac)

Bash se usa para administrar sistemas Linux/macOS y analizar logs.

Comandos básicos:

    ls
    cd
    cat archivo.log
    grep "error" archivo.log
    ps aux

Uso en seguridad:
- revisar logs del sistema  
- encontrar intentos sospechosos  
- filtrar errores  
- monitorear procesos  
- analizar accesos remotos  

Ejemplo de búsqueda de intentos fallidos de autenticación:

    grep -i "failed" /var/log/auth.log

Esto ayuda a detectar fuerza bruta o intentos de acceso no autorizados.

---

# 🟦 4. Python — el lenguaje estándar en ciberseguridad

Python no lo usarás para hacer grandes aplicaciones, sino para:

- automatizar análisis  
- procesar logs  
- crear herramientas pequeñas  
- extraer indicadores de compromiso  

Ejemplo simple (buscar líneas con la palabra ERROR en un archivo de logs):

    with open("logs.txt") as f:
        for line in f:
            if "ERROR" in line:
                print(line)

Esto ya funciona como detección básica de eventos anómalos.

---

# 🟪 5. Regex — expresiones regulares (MUY usadas en SOC y hunting)

Regex (Regular Expression) = patrón de texto para buscar coincidencias.

Ejemplos importantes:

Buscar una dirección IP (vista de forma conceptual, no para memorizar cada símbolo):

- cuatro grupos de números separados por puntos, por ejemplo 192.168.1.10  

Buscar un correo electrónico:

- texto + arroba + dominio + extensión, por ejemplo usuario@empresa.com  

Buscar cualquier número:

- uno o más dígitos seguidos  

Regex se usa en:
- SIEM (Splunk, Sentinel, Wazuh)  
- reglas de detección  
- búsquedas avanzadas  
- análisis de logs  

Saber Regex te coloca por encima del promedio de candidatos porque puedes construir búsquedas mucho más precisas.

---

# 🟫 6. ¿Qué debes recordar para Security+?

Puntos clave:

- PowerShell = cmdlets de administración y análisis en Windows.  
- Bash = administración y análisis de logs en Linux/macOS.  
- Python = automatización flexible en ciberseguridad.  
- Regex = patrón de búsqueda para detectar coincidencias en texto.

Preguntas típicas:

1. ¿Qué lenguaje usa cmdlets como `Get-Process`?  
   ➜ PowerShell  

2. ¿Qué comando se usa para buscar texto en archivos en Linux?  
   ➜ grep  

3. ¿Qué es una expresión regular (Regex)?  
   ➜ Un patrón de búsqueda que permite encontrar texto que cumple ciertas reglas.  

4. ¿Qué lenguaje se usa mucho en automatización en ciberseguridad?  
   ➜ Python  

---

# ⭐ Resumen Final del Día 33

Hoy aprendiste:

- Por qué los scripts son tan importantes en SOC, Threat Hunting y DFIR.  
- Fundamentos de PowerShell para administración y análisis en Windows.  
- Fundamentos de Bash para administración y análisis de logs en Linux/macOS.  
- Uso básico de Python para automatizar análisis de logs.  
- El rol de Regex para búsquedas avanzadas y detecciones más precisas.

Este módulo te acerca directamente a roles mejor pagados como:
- SOC II  
- Threat Hunting Jr  
- DFIR Jr  
- Detection Engineering Jr  

y cubre contenido que aparece tanto en el examen Security+ como en entrevistas técnicas reales.
