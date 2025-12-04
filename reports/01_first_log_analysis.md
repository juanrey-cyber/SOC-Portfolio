# 📝 Reporte 01 – Primer Vistazo a Conexiones y Logs

## 🎯 Objetivo
Hoy intenté ver quién se conecta a la máquina y si hay intentos fallidos de acceso, para empezar a pensar como un analista SOC.  
El objetivo fue entender *dónde* se guarda la información de autenticación y *qué tipo de evidencia* buscaría en un incidente real.

---

## 🧪 Comandos Utilizados
- `who` → muestra usuarios conectados actualmente  
- `last | head -n 10` → historial reciente de sesiones  
- `ls /var/log` → ver archivos de logs disponibles  
- `sudo tail -n 50 /var/log/auth.log` → ver últimos 50 eventos de autenticación  
- Otros comandos de navegación y correcciones según errores del sistema

---

## 👀 Observaciones
- En mi sistema no aparece `/var/log/auth.log`, lo cual es normal en macOS porque no usa ese archivo (es típico de Linux).
- No pude ver intentos de login fallidos, pero entendí claramente *qué buscaría* si existieran.
- Me di cuenta de que muchos comandos pueden fallar dependiendo del sistema operativo, y esto es parte del trabajo real.

---

## 🧠 Análisis Humano (AI-Proof)
- Un error humano suele verse como pocos intentos fallidos distribuidos en el tiempo.  
- Un ataque intencional se vería como múltiples intentos en un período muy corto.  
- Bloquear demasiado rápido sin confirmar podría afectar a un usuario legítimo.  
- Un atacante podría intentar accesos repetidos para descubrir contraseñas o validar credenciales.

---

## ✅ Conclusión
Hoy no encontré un ataque real, pero aprendí dónde buscar evidencia de accesos fallidos y empecé a diferenciar en mi cabeza lo que podría ser un *error humano* vs. *un ataque intencional*.  
Este razonamiento es esencial para los roles SOC y fortalece mi base técnica y analítica.

