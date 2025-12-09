# 🔐 Security+ — Día 32  
# Secure DevOps, CI/CD, Automation & Cloud Security Basics

## 🎯 Objetivo
Comprender cómo se integra la seguridad en DevOps, qué es CI/CD, cómo funcionan los contenedores, cómo se previenen supply-chain attacks, y los fundamentos esenciales de cloud security.  
Este módulo aparece cada vez más en Security+ y entrevistas modernas.

---

# 🟥 1. DevOps vs DevSecOps (explicación fácil)

### ✔ DevOps  
Unión de:
- Development (desarrollo)
- Operations (operaciones)

Objetivo:
- lanzar software rápido  
- automatizar despliegues  
- mejorar velocidad

### ✔ DevSecOps  
Lo mismo que DevOps, pero con **seguridad integrada desde el principio**.

"Securidad como parte del pipeline, no al final."

Ejemplos:
- análisis de código automatizado  
- escaneo de contenedores  
- secrets management  
- pruebas de seguridad antes del deploy  

---

# 🟧 2. CI/CD — Continuous Integration / Continuous Delivery

CI = integrar cambios frecuentemente.  
CD = entregar o desplegar automáticamente.

Pipeline simplificado:
1. Developer sube código  
2. CI ejecuta pruebas  
3. SAST/DAST analiza seguridad  
4. Se construye contenedor o app  
5. CD despliega a producción

Security+:  
➡️ “CI/CD pipelines deben incluir pruebas de seguridad automáticas.”

---

# 🟨 3. Infrastructure as Code (IaC)

Infraestructura descrita en archivos.

Ejemplos:  
- Terraform  
- CloudFormation  
- Ansible  

Beneficios:
- repetible  
- auditable  
- más seguro  
- evita “configuración artesanal”  

Ataques comunes:
- claves secretas en el código  
- permisos excesivos  

---

# 🟦 4. Container Security (Docker, Kubernetes)

Contenedores = aplicaciones empaquetadas con sus dependencias.

### Riesgos:
- imágenes inseguras  
- vulnerabilidades en librerías  
- permisos excesivos  
- secrets dentro del contenedor  

Buenas prácticas:
- usar imágenes oficiales  
- escanear contenedores  
- ejecutar como usuario no root  
- rotación de secrets  

Security+:  
➡️ Contenedores comparten kernel, no están 100% aislados como VMs.

---

# 🟪 5. Supply Chain Attacks (muy importante)

Ataque donde el atacante compromete:
- dependencias  
- librerías  
- proveedores  
- pipelines  

Ejemplo famoso:
- SolarWinds  

Mitigación:
- firmar código  
- escanear dependencias  
- SBOM (Software Bill of Materials)  
- repositorios confiables  

---

# 🟩 6. Automation & Orchestration

Automatización:
- scripts  
- pipelines  
- escaneos programados

Orquestration:
- Kubernetes  
- herramientas que gestionan múltiples contenedores

Ventajas:
- rapidez  
- consistencia  
- menos errores humanos  

---

# 🟫 7. Cloud Security — Fundamentos (MUY preguntado)

## 🔸 Shared Responsibility Model (CRÍTICO)
**Cloud Provider (AWS, Azure, GCP):**  
- seguridad de la infraestructura  
- hardware  
- red  
- disponibilidad  

**Cliente (tú/la empresa):**  
- configuración  
- IAM  
- datos  
- seguridad del sistema operativo  
- cifrado  

Security+:  
➡️ fallas en cloud casi siempre son errores de CONFIGURACIÓN del cliente.

---

# 🟦 8. Cloud Types

### ✔ Public Cloud  
AWS / Azure / GCP  
Recursos compartidos.

### ✔ Private Cloud  
Infraestructura exclusiva de la empresa.

### ✔ Hybrid Cloud  
Mezcla de ambas.

### ✔ Community Cloud  
Organizaciones con necesidades similares comparten cloud.

---

# 🟩 9. Cloud Service Models (MUY preguntado)

### ✔ IaaS — Infrastructure as a Service  
Tú gestionas:
- OS  
- apps  
- datos  

Proveedor gestiona:
- hardware  
- red  
- almacenamiento  

Ejemplo: AWS EC2.

---

### ✔ PaaS — Platform as a Service  
Tú gestionas:
- datos  
- apps  

Proveedor gestiona:
- OS  
- hardware  
- runtime  

Ejemplo: Heroku, Firebase.

---

### ✔ SaaS — Software as a Service  
Todo gestionado por el proveedor.  
Ejemplo: Gmail, Office 365.

Security+:  
➡️ SaaS = responsabilidad mínima del cliente.  
➡️ IaaS = responsabilidad máxima del cliente.

---

# 🟫 10. Serverless (FaaS)

Ejemplos:
- AWS Lambda  
- Azure Functions  

Ventajas:
- no gestionas servidores  
- escalabilidad automática  

Riesgos:
- ejecución excesiva (DoS)  
- permisos IAM mal configurados  

---

# 🟩 11. Secrets Management (muy importante)

NUNCA guardar:
- claves API  
- tokens  
- credenciales  
- passwords  

En:
- repositorios  
- contenedores  
- pipelines  
- archivos de configuración

Soluciones:
- AWS Secrets Manager  
- Hashicorp Vault  

---

# 🟦 12. Mini-Práctica tipo Security+

**1. ¿Qué modelo implica que la seguridad se incluya desde desarrollo?**  
→ DevSecOps

**2. ¿Qué servicio ofrece infraestructura y deja al cliente gestionar el OS?**  
→ IaaS

**3. ¿Qué ataque compromete dependencias o proveedores?**  
→ Supply chain attack

**4. ¿Qué herramienta detecta vulnerabilidades antes del deploy?**  
→ SAST/DAST en CI/CD

**5. ¿Qué cloud model tiene menos responsabilidad para el cliente?**  
→ SaaS

---

# ⭐ Resumen Final
Hoy aprendiste:
- DevSecOps vs DevOps  
- CI/CD seguro  
- IaC  
- Seguridad de contenedores  
- Supply-chain attacks  
- Automatización  
- Shared Responsibility Model  
- IaaS vs PaaS vs SaaS  
- Serverless  
- Secrets management  

Este módulo es crítico para entrevistas modernas y el examen Security+.
