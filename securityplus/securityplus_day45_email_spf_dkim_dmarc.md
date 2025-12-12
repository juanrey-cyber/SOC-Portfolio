# 🔐 Security+ — Día 45  
# Email Security, Anti-Phishing, SPF, DKIM, DMARC (explicado fácil)

## 🎯 Objetivo
Entender cómo se protege el correo contra spoofing y phishing mediante SPF, DKIM y DMARC. Es contenido crucial para roles SOC, Cloud Security y Threat Hunting.

---

# 🟥 1. ¿Cuál es el problema?
El email originalmente no tenía seguridad. Cualquiera podía enviar mensajes haciéndose pasar por:
- bancos
- empresas
- ejecutivos
- autoridades

Esto se llama spoofing y permite phishing, fraude y ransomware.

Para solucionar esto existen tres controles:
SPF, DKIM y DMARC.

---

# 🟧 2. SPF (Sender Policy Framework)
SPF define qué servidores están autorizados a enviar correo en nombre de un dominio.

Ejemplo de registro SPF:
v=spf1 include:_spf.google.com -all

Significa:
“Solo Google puede enviar emails usando mi dominio; cualquier otro servidor debe ser rechazado.”

SPF combate:
- spoofing de dirección
- spam fingiendo ser tu dominio

---

# 🟨 3. DKIM (DomainKeys Identified Mail)
DKIM agrega una firma digital al email.

El servidor emisor firma el mensaje con una llave privada.  
El receptor verifica la firma con la llave pública guardada en DNS.

Si falla:
- el mensaje fue alterado
- o el remitente es falso

DKIM protege:
- integridad del mensaje
- autenticidad del remitente

---

# 🟦 4. DMARC (Domain-based Message Authentication, Reporting & Conformance)
DMARC combina SPF + DKIM y agrega reglas de qué hacer si alguno falla.

Ejemplo de registro DMARC:
v=DMARC1; p=reject; rua=mailto:seguridad@empresa.com

Interpretación:
“Si SPF y DKIM fallan, rechaza el mensaje. Además, envíame reportes de intentos de suplantación.”

Modos de política:
- none → solo monitoreo
- quarantine → mandar a spam
- reject → bloquear completamente

DMARC evita:
- spoofing directo
- fraude tipo CEO/BEC
- phishing con dominios falsos

---

# 🟪 5. Cómo trabajan juntos SPF + DKIM + DMARC

SPF responde: “¿Quién puede enviar en nombre del dominio?”  
DKIM responde: “¿Está firmando correctamente el correo?”  
DMARC responde: “¿Qué hago si falla? ¿Bloqueo, pongo en spam o solo monitoreo?”

Los dominios seguros usan los 3.

---

# 🟫 6. Señales reales de phishing en SOC

1. SPF fail → servidor no autorizado envió el email.  
2. DKIM fail → contenido manipulado o remitente falso.  
3. DMARC fail → política indica rechazo o spam.  
4. URLs sospechosas → dominios raros, acortadores o caracteres inusuales.  
5. Adjuntos peligrosos → zip, html, iso, js, img.  
6. Tono de urgencia → presión psicológica (“urgente”, “cuenta bloqueada”, “pago pendiente”).  

---

# 🟩 7. Preguntas de entrevista

¿Qué es SPF?  
→ Lista de servidores autorizados para enviar correo en nombre de un dominio.

¿Qué es DKIM?  
→ Firma digital del correo para verificar integridad y autenticidad.

¿Qué es DMARC?  
→ Política que define qué hacer si SPF/DKIM fallan y genera reportes de intentos de spoofing.

¿Cuál protege más?  
→ DMARC.

¿Cómo detectas phishing?  
→ SPF fail, DKIM fail, DMARC fail, enlaces raros, adjuntos sospechosos, urgencia inusual.

---

# ⭐ Resumen Día 45
Aprendiste:
- cómo funcionan SPF, DKIM y DMARC
- cómo protegen contra spoofing y phishing
- detecciones reales en SOC
- respuestas típicas de entrevista

Tema crítico para roles SOC II, Cloud Security y Threat Hunting.
