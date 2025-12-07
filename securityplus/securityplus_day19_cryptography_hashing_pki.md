# 🔐 Security+ — Día 19  
# Cryptography, Hashing, Certificates & PKI

## 🎯 Objetivo
Dominar los fundamentos de criptografía moderna: hashing, cifrado simétrico/asimétrico, certificados digitales, claves públicas y privadas, PKI y conceptos críticos para examenes y roles SOC.

---

# 🟦 1. Hashing (INTEGRIDAD)

## ✔ Qué es hashing?
Transformación de datos → resultado único y no reversible.

## ✔ Propósito
- Garantizar integridad  
- Detectar modificaciones  
- Verificar archivos  

## ✔ Características
- **Unidireccional (no reversible)**  
- **Determinístico** (mismo input = mismo hash)  
- **Avalancha**: pequeños cambios producen hashes totalmente distintos  

## ✔ Algoritmos comunes
- **SHA-256** (estándar moderno)  
- SHA-1 (roto)  
- MD5 (roto)  

## ✔ Importante
Hash ≠ Cifrado  
El hash NO se puede descifrar.

---

# 🟥 2. Cifrado Simétrico (misma clave)

## ✔ Cómo funciona?
Una única clave sirve para:
- cifrar  
- descifrar  

Muy rápido y eficiente.

## ✔ Algoritmo principal:
- **AES** (estándar moderno)  
  - AES-128  
  - AES-192  
  - AES-256 (más seguro)

## ✔ Uso típico:
- VPN  
- discos cifrados  
- comunicaciones internas  

---

# 🟩 3. Cifrado Asimétrico (clave pública + privada)

## ✔ Cómo funciona?
Tiene dos claves:
- **Clave pública** → compartir con todos  
- **Clave privada** → mantener secreta  

Lo que cifra una → solo la otra puede descifrar.

## ✔ Usos:
- HTTPS  
- TLS  
- Firma digital  
- Intercambio de claves  

## ✔ Algoritmos:
- RSA (más usado históricamente)  
- ECC (Elliptic Curve, moderno y más rápido)  
- Diffie-Hellman (intercambio de claves)

---

# 🟧 4. Firma Digital (NO es cifrado)

La firma digital sirve para:
- autenticidad  
- integridad  
- no repudio

## Cómo funciona?
1. Se hace hash del mensaje  
2. Se cifra el hash con **clave privada** del remitente  
3. El receptor valida con la **clave pública**

Si coincide → está verificado.

---

# 🟪 5. Certificados Digitales (X.509)

Un certificado contiene:
- clave pública  
- nombre del dueño  
- fecha de expiración  
- firma de la CA  
- número de serie  

Tipos comunes:
- DV (Domain Validation)  
- OV (Organization Validation)  
- EV (Extended Validation, más estricto)  

---

# 🟫 6. PKI (Public Key Infrastructure)

Es el sistema completo que administra certificados.

Componentes:
- **CA (Certificate Authority)**  
  Firma y emite certificados  

- **Intermediate CA**  
  Delegación de confianza  

- **CRL (Certificate Revocation List)**  
  Lista de certificados inválidos  

- **OCSP**  
  Validación en tiempo real  

- **Key Escrow**  
  Almacenamiento seguro de claves  

---

# 🟨 7. Perfect Forward Secrecy (TLS moderno)

Garantiza que si una clave privada se filtra, las sesiones pasadas NO se pueden descifrar.

Usa:
- Diffie-Hellman  
- ECDHE (lo más moderno)

---

# 🔵 8. SSL vs TLS

## SSL = MALO, obsoleto  
Nunca usar.

## TLS = moderno  
Usar:
- TLS 1.2  
- TLS 1.3 (ideal)

---

# 🧭 9. Qué mira SOC sobre criptografía?

- certificados expirados  
- fallas SSL/TLS  
- uso de protocolos débiles (TLS 1.0, SSL3)  
- tráfico no cifrado  
- ataques MITM  
- firmas digitales inválidas  
- OCSP oculta o fallando  

Ejemplo real común:
- token robado porque la aplicación no usa HTTPS  

---

# 📝 10. Mini-Práctica

**1. ¿Qué algoritmo simétrico es estándar moderno?**  
➡️ AES

**2. ¿Para qué sirve hashing?**  
➡️ Integridad

**3. ¿Qué clave se usa para firmar digitalmente?**  
➡️ Privada

**4. ¿Cómo se valida una firma?**  
➡️ Con la clave pública

**5. ¿Qué reemplaza SSL?**  
➡️ TLS

---

# ⭐ Resumen Final
- Hashing = integridad  
- Cifrado simétrico = velocidad  
- Cifrado asimétrico = intercambio seguro + firmas  
- PKI = infraestructura completa de certificados  
- TLS moderno usa ECDHE para seguridad avanzada  
- Todo este contenido es clave para Security+ y SOC  

