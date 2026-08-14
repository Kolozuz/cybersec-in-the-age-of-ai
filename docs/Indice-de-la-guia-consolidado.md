## Arquitectura

10 capítulos

0. Contexto y modelos mentales
    ```
    1. Concepto
       ├── ¿Qué es ciberseguridad?
       ├── Activo
       ├── Amenaza
       ├── Vulnerabilidad
       ├── Riesgo
       └── Threat Modeling
    2. Amenaza
       └── El mismo activo puede tener múltiples caminos de ataque
    3. Ejemplo
       └── La cuenta corporativa comprometida
           ↓
           hilo conductor de la guía
    4. Control
       ├── Control ≠ herramienta
       ├── Defense in Depth
       ├── Least Privilege
       ├── Assume Breach
       └── Prevenir → Detectar → Responder → Recuperar
    5. El lente de la IA
       ├── Amplifica capacidades
       ├── Introduce superficies
       ├── Cambia capacidades ofensivas/defensivas
       └── Cambia el threat model
    6. Takeaways
       └── Una idea central + 5 principios
    7. Fuentes
    ```
1. Identidad y acceso
    ```
                     IDENTIDAD Y ACCESO
                            │
            ┌───────────────┴───────────────┐
            ↓                               ↓
       AUTENTICACIÓN                   AUTORIZACIÓN
            │                               │
       Contraseñas                        RBAC
       Password Managers                  ABAC
       MFA                                ReBAC
       Passkeys                           Least Privilege
       Recovery                           Deny by Default
       Sessions                           BOLA
            │                               │
            └───────────────┬───────────────┘
                            ↓
                           IA
                            │
                  ┌─────────┴─────────┐
                  ↓                   ↓
           Ataques de identidad   Agentes y permisos
    ```
2. Datos y privacidad
    ```
                     ¿QUÉ ESTOY PROTEGIENDO?
                               │
                 ┌─────────────┴─────────────┐
                 ↓                           ↓
              DATOS                       SECRETS
                 │                           │
           Clasificar                    Proteger
           Minimizar                     Rotar
           Controlar                     Revocar
           Cifrar                        Auditar
                 │                           │
                 └─────────────┬─────────────┘
                               ↓
                              IA
                               │
                 ┌─────────────┴─────────────┐
                 ↓                           ↓
           ¿Qué le doy?               ¿Qué puede revelar?
                 ↓                           ↓
           Minimización             Sensitive Information
           + clasificación               Disclosure
    ```
3. Cifrado, redes y navegación
   El capítulo debería responder principalmente:

   ¿Desde dónde estoy accediendo y qué pasa si ese dispositivo se compromete?

   Mantendría el alcance conceptual para el público general, pero con suficiente profundidad técnica para nuestros compañeros:

   endpoint como superficie de ataque;
   actualizaciones y vulnerabilidades;
   malware;
   aplicaciones y software de fuentes confiables;
   navegador y extensiones;
   permisos de aplicaciones;
   dispositivos personales vs. corporativos;
   cifrado del dispositivo;
   bloqueo y protección física;
   backups;
   USB y dispositivos externos;
   EDR/antivirus, explicado conceptualmente;
   y, como puente hacia los capítulos siguientes, descargas y software malicioso.

   Para el lente de IA, me parece especialmente interesante cubrir:

   malware generado o asistido por IA;
   mayor capacidad de personalización de ataques;
   deepfakes como problema de confianza en el endpoint;
   asistentes de código y el riesgo de introducir código inseguro;
   software generado por IA que los usuarios descargan o ejecutan sin comprenderlo;
   y cómo la IA también puede mejorar detección, análisis y respuesta.

   No profundizaría todavía en redes/VPN ni en ingeniería social: así evitamos adelantarnos a los capítulos donde esos conceptos tendrán más peso.
   ```
                     REDES
                     │
         ┌────────────┼────────────┐
         ↓            ↓            ↓
      Internet       TLS          Wi-Fi
         │            │            │
         ↓            ↓            ↓
      exposición   protección   confianza
         │            │            │
         └────────────┼────────────┘
                     ↓
                  Zero Trust
                     ↓
               acceso a recursos
                     ↓
                     IA
   ```
   hay una conexión particularmente buena con los dos capítulos anteriores:

   Cap. 1: ¿Quién eres y qué puedes hacer?
   Cap. 2: ¿Qué estás protegiendo?
   Cap. 3: ¿Por dónde viaja? 
4. Software, dispositivos y malware
   Este capítulo está cumpliendo ahora mismo una función deliberadamente amplia: explicar cómo pensar sobre software como superficie de confianza.

   Hay dos temas que aparecen pero que no deberíamos desarrollar demasiado todavía: 
   ```
   Cap. 4 Software
      │
      ├── consumo de software
      ├── malware
      ├── dependencias
      └── supply chain
               │
               └─────────────┐
                              ↓
                     Cap. 8 Desarrollo
                              │
                     construir software
                     seguro desde el diseño
   ```
   Y lo mismo ocurre con malware:
   ```
   Cap. 4 → ¿Cómo evito ejecutar malware?
   Cap. 6 → ¿Qué hago si fui comprometido? 
   ```
5. Ingeniería social y confianza
   Este capítulo deja planteada una idea que puede terminar convirtiéndose en **uno de los mensajes centrales de toda la guía**:

   ```text
                     SEGURIDAD
                           │
               ┌──────────┴──────────┐
               ↓                     ↓
         ¿Puedo confiar?       ¿Puedo verificar?
               │                     │
         señales humanas       controles técnicos
               │                     │
               └──────────┬──────────┘
                           ↓
                        IA
                           │
               las señales son
                  más fáciles
                  de falsificar
                           ↓
                     VERIFICACIÓN
   ```

   Y además establece una progresión muy limpia con los capítulos anteriores:

   **Cap. 1 — Identidad:**

   > ¿Quién eres?

   **Cap. 2 — Datos:**

   > ¿Qué estás protegiendo?

   **Cap. 3 — Redes:**

   > ¿Por dónde viaja?

   **Cap. 4 — Software:**

   > ¿Qué estás ejecutando?

   **Cap. 5 — Ingeniería social:**

   > **¿En quién o en qué estás confiando?**
6. Resiliencia y respuesta
   ```
   1. Concepto
      └── Prevención ≠ resiliencia
      └── Incident response / recovery
   2. Amenaza
      └── ¿Qué pasa cuando la prevención falla?
   3. Ejemplo
      └── Cuenta comprometida
   4. Control
      ├── Backups
      ├── Plan de respuesta
      ├── Contención
      └── Post-incident
   5. El lente de la IA
      ├── IA acelera ataques
      ├── IA acelera respuesta
      └── El tiempo de respuesta importa más
   6. Takeaways
   7. Fuentes
   ```
7. Seguridad de sistemas de IA
   ```
   1. Concepto
      ├── ¿Qué es un sistema de IA?
      ├── ¿Qué lo diferencia del software tradicional?
      └── Modelo → datos → herramientas → acciones
   2. Amenaza
      ├── Input / prompt injection
      ├── Contexto y datos
      ├── Output
      ├── Tools y acciones
      └── Modelo / supply chain
   3. Ejemplo
      └── Asistente corporativo + documentos internos
         └── indirect prompt injection
   4. Control
      ├── Separar instrucciones y datos
      ├── Least privilege
      ├── Human-in-the-loop
      ├── Validación de outputs
      ├── Control de herramientas
      └── Observabilidad
   5. El lente de la IA
      ├── Naturaleza probabilística
      ├── Prompt injection
      ├── Confused deputy
      ├── Agentes
      └── Threat modeling para IA
   6. Takeaways
   7. Fuentes
   ```
8. Desarrollo seguro
   ```
   1. Concepto
      ├── Secure SDLC
      ├── Security by Design
      └── Threat Modeling

   2. Amenaza
      ├── Diseño
      ├── Código
      ├── Dependencias / Supply Chain
      ├── CI/CD
      └── Operación

   3. Ejemplo
      └── File upload

   4. Control
      ├── Threat Modeling
      ├── Secure Coding
      ├── Dependency / Supply Chain Security
      ├── Code Review
      └── Security Testing

   5. El lente de la IA
      ├── IA como herramienta de desarrollo
      ├── Código generado por IA
      ├── IA como superficie de ataque
      ├── Agentes / Tools
      └── Nuevo Threat Model

   6. Takeaways

   7. Fuentes
   ```
9. Guía del viajero digital
   subtitle: de novato a power user
   ```
   1. Introducción
      └── Que no cunda el panico! 
   2. Viajero digital novato
      ├── Cuentas
      ├── Phishing
      ├── Updates
      ├── Descargas
      ├── Backups
      └── Kit mínimo
   3. Viajero digital intermedio
      ├── Revisión de cuentas
      ├── MFA / passkeys
      ├── Dispositivos
      ├── Redes / VPN
      ├── Navegación
      └── Códigos QR
   4. Viajero digital Power User
      ├── Identidades
      ├── Permisos
      ├── Cifrado
      ├── Computación cuántica
      ├── Viajes
      └── IA y privacidad
   5. Power User+
      ├── Hardware security keys
      ├── DNS / networking
      ├── Segmentación
      ├── Backups avanzados
      └── Hardening
   6. Si eres desarrollador
      ├── Secure development checklist
      └── Desarrollo asistido por IA
   7. IA como copiloto
      ├── Entender
      ├── Revisar
      ├── Priorizar
      └── Verificar
   8. ¿Dónde estoy?
      └── Matriz de niveles
   9. Checklist final
      └── Mi kit del viajero digital
   ```