# Auditoría de alcance — v1

## 1. Contexto y modelos mentales

### Objetivo

Dar al lector un **modelo mental para pensar en seguridad**, en lugar de comenzar inmediatamente con herramientas y buenas prácticas.

Este capítulo debería responder:

> **¿Cómo piensa un profesional de ciberseguridad sobre un problema?**

### Esencial

* Qué es un activo
* Qué es una amenaza
* Qué es una vulnerabilidad
* Qué es un riesgo
* Impacto vs. probabilidad
* Controles
* CIA Triad
* Defense in Depth
* Least Privilege
* Assume Breach

No intentaría explicar todos estos conceptos con profundidad académica. El objetivo es que el lector pueda reconocerlos y utilizarlos.

### Técnico

Aquí sí introduciría:

* Threat modeling
* Attack surface
* Attack vectors
* Trust boundaries
* Risk-based thinking

Pero probablemente **Threat Modeling merece desarrollo real en el capítulo 9**, mientras que aquí sólo introducimos el concepto.

### Lente IA

Este es uno de los capítulos donde la IA debe tener un papel especialmente conceptual.

La pregunta central:

> **¿Cómo cambia nuestro threat model cuando una máquina puede generar, analizar y ejecutar acciones a escala?**

Ejemplos:

* ataque automatizado
* phishing personalizado
* generación de código
* agentes con herramientas
* aumento de superficie de ataque

### Fuera de alcance

Evitaría:

* frameworks completos de risk management
* ISO 27001
* metodologías cuantitativas de riesgo
* compliance

Pueden aparecer como referencias, pero no son el objetivo.

### Peso

**Medio.**

Es fundamental para entender el resto, pero no debería consumir demasiadas slides.

---

# 2. Identidad y acceso

Este es uno de los capítulos **más importantes de toda la guía**.

### Objetivo

Que el lector entienda que proteger una cuenta no consiste simplemente en "tener una contraseña difícil".

### Esencial

* Identidad
* Authentication
* Authorization
* Contraseñas
* Password reuse
* Password managers
* MFA
* Passkeys
* Recovery mechanisms
* Credential theft

Aquí encajan perfectamente las ideas originales de:

* contraseñas
* qué hace segura una contraseña
* gestores de contraseñas

que estaban presentes desde tu primer bosquejo. 

### Técnico

* Password hashing
* Credential stuffing
* Brute force
* Session/token theft
* OAuth/OIDC, al menos conceptualmente
* IAM
* RBAC/ABAC
* Least privilege

No convertiría OAuth/OIDC en un tutorial. Lo importante es entender qué está pasando cuando hacemos "Sign in with Google", por ejemplo.

### IA

Aquí tenemos muchísimo material:

* phishing generado por IA
* spear phishing personalizado
* credential theft
* social engineering
* voice cloning
* deepfake identity
* automated account attacks

Y una conexión especialmente importante:

> **La IA no necesariamente rompe la autenticación; puede atacar al usuario que se encuentra detrás de ella.**

### Fuera de alcance

No haría un tratado sobre:

* Active Directory
* Kerberos
* SAML
* PAM
* IAM cloud específico

Podrían aparecer en la ruta profesional si después vemos que nuestra audiencia lo necesita.

### Peso

**Muy alto.**

Probablemente uno de los capítulos centrales de la presentación.

---

# 3. Datos y privacidad

Este capítulo no estaba explícito en tu lluvia de ideas, pero ahora considero que es **necesario** para una guía sobre ciberseguridad en la era de IA.

### Objetivo

Cambiar la pregunta:

> "¿Estoy usando una herramienta segura?"

por:

> **"¿Qué información estoy entregando y qué consecuencias tendría que se filtrara?"**

### Esencial

* Datos personales
* Datos sensibles
* Información confidencial
* Información corporativa
* Credentials
* Secrets
* API keys
* Tokens
* Metadata

### Técnico

* Data classification
* Secrets management
* Data minimization
* Access control
* Data at rest / in transit
* DLP

### IA

Aquí está probablemente **uno de los mayores valores de la guía**.

* ¿Qué puedo poner en un chatbot?
* Shadow AI
* Información corporativa en modelos externos
* Código propietario
* PII
* Prompts que contienen secretos
* Retención de datos
* Enterprise AI
* Data leakage

También debemos distinguir:

> **"El modelo sabe algo" ≠ "el proveedor está entrenando el modelo con mis datos".**

Es un área donde debemos ser extremadamente precisos cuando lleguemos a redactar.

### Fuera de alcance

No convertiría este capítulo en:

* legislación de privacidad
* GDPR
* política corporativa
* privacidad personal extrema
* anonimato digital

Es seguridad de datos, no un manual jurídico de privacidad.

### Peso

**Alto.**

Especialmente para una empresa tecnológica.

---

# 4. Cifrado, redes y navegación

Aquí agrupamos varios elementos originales:

* encriptación
* navegación online
* VPNs
* computadores cuánticos



### Objetivo

Explicar **qué ocurre con los datos cuando viajan entre sistemas** y qué mecanismos tenemos para protegerlos.

### Esencial

* Encryption
* HTTPS
* TLS
* Certificados
* Wi-Fi
* Redes públicas
* VPN
* DNS

Y una distinción imprescindible:

> **Cifrado ≠ hashing ≠ encoding**

### Técnico

* Symmetric encryption
* Asymmetric encryption
* Public/private keys
* PKI
* TLS handshake
* DNS
* VPN tunneling
* MITM

Aquí sí podemos permitirnos algo más de profundidad porque la audiencia es técnica.

### VPN

Un pequeño bloque específico:

**Qué hace una VPN / qué no hace una VPN.**

La idea sería combatir el mito:

> VPN = seguridad/anonymity.

### Quantum

Un **deep dive**, no el eje del capítulo:

* RSA/ECC
* Shor
* Grover
* Post-Quantum Cryptography
* Harvest Now, Decrypt Later

### IA

Aquí el vínculo con IA es más indirecto.

No intentaría inventar una conexión artificial. Podemos hablar de:

* nuevas superficies de comunicación
* infraestructura de IA
* protección de datos enviados a APIs
* tráfico entre agentes, tools y servicios

### Fuera de alcance

* matemáticas profundas de criptografía
* implementación de algoritmos
* construir una VPN
* configuración avanzada de routers

### Peso

**Alto**, pero probablemente con algunos contenidos técnicos opcionales.

---

# 5. Software, dispositivos y malware

### Objetivo

Enseñar al lector a controlar **qué software ejecuta y qué puede hacer ese software**.

### Esencial

* Descargas
* Fuentes confiables
* Actualizaciones
* Browser extensions
* Archivos adjuntos
* Malware
* Ransomware
* Infostealers
* Software pirata/crackeado
* QR/Quishing como referencia

Esto recoge directamente una de las preocupaciones originales de la guía: *cómo evitar descargar programas maliciosos*. 

### Técnico

* CVEs
* Exploits
* Zero-days
* Dependency vulnerabilities
* Sandboxing
* Code signing
* EDR/XDR — quizá sólo conceptualmente
* Software supply chain

### IA

* Malware-assisted development
* Automated campaigns
* AI-generated phishing payloads
* Fake applications
* Malicious packages
* AI-assisted vulnerability discovery

Pero tendría cuidado de no caer en la narrativa de:

> "La IA crea malware mágico."

El mensaje debería ser más riguroso:

> **La IA puede aumentar las capacidades de actores que ya poseen conocimientos y herramientas ofensivas.**

### Fuera de alcance

No explicaría cómo desarrollar malware ni explotación práctica.

### Peso

**Alto.**

Especialmente bueno para una presentación porque permite usar ejemplos visuales.

---

# 6. Ingeniería social y confianza

Este probablemente sea **el capítulo más importante desde el punto de vista del lente IA**.

Y aquí, como acordamos, estará el desarrollo profundo de phishing.

### Objetivo

Explicar que muchas intrusiones no empiezan explotando una vulnerabilidad técnica, sino **manipulando a una persona**.

### Esencial

* Social engineering
* Phishing
* Spear phishing
* Smishing
* Vishing
* Baiting
* Pretexting
* Impersonation

### El modelo del ataque

Podemos enseñar algo muy sencillo:

```text
Información
    ↓
Confianza
    ↓
Manipulación
    ↓
Acción de la víctima
    ↓
Acceso / información / dinero
```

Esto es mucho más útil que simplemente memorizar "red flags".

### Técnico

* Business Email Compromise
* Credential phishing
* OAuth consent phishing
* Session hijacking
* Social engineering targeting privileged users

### IA

Aquí está el verdadero "jugo":

* mensajes personalizados
* traducción automática
* voice cloning
* deepfake video
* synthetic identities
* automated reconnaissance
* fake personas
* real-time social engineering

Y una idea que puede convertirse en slide:

> **La IA reduce el costo de personalizar el engaño.**

### QR

Aquí colocaría definitivamente **QR / Quishing**.

No como una tecnología especial, sino como otro canal de ingeniería social.

### Fuera de alcance

No necesitamos catalogar cada variante imaginable de phishing.

### Peso

**Muy alto.**

Probablemente **uno de los 3 capítulos más importantes de toda la presentación**.

---

# 7. Resiliencia y respuesta

Como acordamos, **capítulo corto**.

### Objetivo

Introducir una idea que a veces falta en las guías para usuarios:

> **La seguridad perfecta no existe. Hay que prepararse también para el fallo.**

### Esencial

* Backups
* Recovery
* Ransomware
* Incident
* Containment
* Recovery
* Reporting

### Técnico

Sólo introduciría:

* RPO
* RTO
* Disaster Recovery
* Business Continuity
* Immutable backups

Sin profundizar demasiado.

### IA

* ataques automatizados
* velocidad de propagación
* necesidad de detección rápida
* AI-assisted detection/response

Y algo más interesante:

> **¿Qué pasa si un sistema autónomo toma una acción incorrecta durante un incidente?**

Esto conecta con los capítulos de agentes.

### Fuera de alcance

No convertirlo en un SOC handbook.

Nada de:

* SIEM profundo
* playbooks extensos
* forensics
* threat hunting avanzado

### Peso

**Medio-bajo.**

Pero conceptualmente necesario.

---

# 8. Seguridad de sistemas de IA

Aquí empieza la especialización real.

### Objetivo

Responder:

> **¿Cómo aseguramos una aplicación cuyo comportamiento depende de un modelo de IA?**

### Esencial

Primero necesitamos enseñar la arquitectura:

```text
Usuario
   ↓
Aplicación
   ↓
Modelo
   ↓
Datos / RAG
   ↓
Tools / APIs
   ↓
Sistemas externos
```

Esto permitirá que los ataques posteriores tengan contexto.

### Conceptos principales

* Prompt Injection
* Sensitive Information Disclosure
* Insecure Output Handling
* System Prompt Leakage
* Data Poisoning
* Model Poisoning
* Supply Chain
* Excessive Agency
* Improper Access Control

Aquí utilizaría **OWASP como una de las fuentes estructurales principales**, especialmente para evitar crear una taxonomía propia cuando ya existen marcos reconocidos.

### RAG

* embeddings
* vector databases
* retrieval
* access control
* poisoned documents
* indirect prompt injection

### Agents

Este tema merece bastante atención:

* tools
* permissions
* autonomy
* action space
* human-in-the-loop
* least privilege

### Técnico

Aquí sí queremos hablar con propiedad de:

* model serving
* APIs
* orchestration
* tool calling
* vector stores
* evaluation
* monitoring
* guardrails

### Fuera de alcance

No convertiría esto en un curso de:

* machine learning
* entrenamiento de modelos
* matemática de redes neuronales
* arquitectura de Transformers

El lector debe entender **cómo se puede atacar un sistema de IA**, no necesariamente cómo construir un modelo desde cero.

### Peso

**Muy alto para la audiencia técnica; medio para el resto.**

Aquí tiene sentido que exista una ruta especializada.

---

# 9. Desarrollo seguro

Este capítulo debe hablar directamente a nuestros compañeros que construyen software.

### Objetivo

Mostrar que:

> **La IA no elimina las prácticas de Secure SDLC; las hace todavía más importantes.**

### Esencial

* Secure by Design
* Threat Modeling
* Input validation
* Output validation
* Authentication
* Authorization
* Least privilege
* Secrets management
* Dependency management

### Técnico

Aquí sí entran:

* SAST
* DAST
* SCA
* SBOM
* CI/CD security
* Container security
* Cloud security
* IaC
* API security
* Software supply chain

### IA aplicada al desarrollo

Esta es probablemente la parte más relevante:

* AI coding assistants
* código generado por IA
* hallucinated APIs
* insecure code
* vulnerable dependencies
* secrets en prompts
* review asistido por IA
* automated testing
* AI-assisted security

La pregunta no debería ser:

> "¿La IA escribe código seguro?"

sino:

> **"¿Cómo cambia nuestro proceso de desarrollo cuando una IA participa en él?"**

### Fuera de alcance

No intentaría cubrir todo AppSec.

Por ejemplo:

* pentesting avanzado
* explotación manual
* reverse engineering
* malware analysis

Podrían aparecer como referencias externas.

### Peso

**Muy alto para la audiencia técnica.**

---

# 10. Guía práctica — El viajero digital

Esta sección no debería introducir conceptos nuevos.

Ese punto me parece **muy importante**.

Debe ser una **destilación accionable de todo lo anterior**.

### Nivel 1 — Novato

Objetivo:

> **Reducir rápidamente los riesgos más comunes.**

* Password manager
* MFA
* Updates
* Backups
* Phishing
* Downloads
* Device security

### Nivel 2 — Intermedio

> **Pasar de buenas prácticas aisladas a una postura de seguridad.**

* Passkeys
* Security keys
* Encryption
* Recovery codes
* VPN
* Privacy
* Backup strategy
* Account management

### Nivel 3 — Power User

> **Construir una estrategia personal.**

* Threat modeling
* Compartmentalization
* Sandboxing
* Secure networking
* Advanced authentication
* Monitoring

### Nivel 4 — Profesional técnico

> **Aplicar seguridad al trabajo tecnológico.**

* Secrets
* IAM
* Cloud
* Dependencies
* CI/CD
* APIs
* Supply chain
* Secure SDLC

### Nivel 5 — AI Builder

> **Construir sistemas de IA de manera segura.**

* Prompt injection
* RAG security
* Agent security
* Tool permissions
* Data security
* Model supply chain
* Monitoring
* Evaluation

### Peso

**Muy alto como herramienta de presentación**, aunque no como capítulo conceptual.

---

# Resultado de la auditoría

Después de pasar los diez capítulos por este filtro, mi evaluación sería:

| Capítulo                            | Prioridad    | Profundidad  | Papel                  |
| ----------------------------------- | ------------ | ------------ | ---------------------- |
| 0. Contexto y modelos mentales      | Alta         | Media        | Fundamentación         |
| 1. Identidad y acceso               | **Muy alta** | Alta         | Fundamental            |
| 2. Datos y privacidad               | **Muy alta** | Alta         | Fundamental + IA       |
| 3. Cifrado, redes y navegación      | Alta         | Alta         | Fundamental + técnico  |
| 4. Software, dispositivos y malware | Alta         | Alta         | Fundamental + práctico |
| 5. Ingeniería social y confianza    | **Muy alta** | Alta         | Fundamental + IA       |
| 6. Resiliencia y respuesta          | Media        | Baja         | Complementario         |
| 7. Seguridad de sistemas de IA      | **Muy alta** | **Muy alta** | Especialización        |
| 8. Desarrollo seguro                | **Muy alta** | **Muy alta** | Especialización        |
| 9. El viajero digital               | **Muy alta** | Variable     | Acción                 |

## Y veo cuatro "pilares" de la guía

Si tuviera que resumir la arquitectura en una sola diapositiva, diría que la guía gira alrededor de:

**IDENTIDAD**
¿Quién eres y quién puede acceder?

**DATOS**
¿Qué estás protegiendo y dónde están?

**CONFIANZA**
¿Cómo sabes que algo o alguien es legítimo?

**SISTEMAS**
¿Cómo construyes y operas tecnología de forma segura?

Y la IA atraviesa los cuatro:

> **La IA cambia cómo atacamos, cómo defendemos y qué necesitamos proteger.**
