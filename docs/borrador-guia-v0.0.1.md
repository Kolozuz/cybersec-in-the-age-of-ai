# Capítulo 0 — Contexto y modelos mentales

> **Antes de aprender herramientas, aprende a pensar en términos de riesgo.**

La ciberseguridad no consiste en eliminar todos los riesgos. Eso no es posible.

Consiste en **identificar qué queremos proteger, entender qué podría salir mal y aplicar controles que reduzcan la probabilidad o el impacto de esos escenarios**.

Este modelo de pensamiento será el hilo conductor del resto de la guía.

---

## 1. Concepto

### ¿Qué es ciberseguridad?

Podemos entender la ciberseguridad como la disciplina de **proteger sistemas, datos, servicios y personas frente a amenazas digitales**, reduciendo la probabilidad y el impacto de incidentes.

Esta definición contiene una idea importante: **seguridad no significa ausencia de riesgo**.

En cualquier sistema habrá riesgos. La pregunta profesional es:

> **¿Cuáles importan, qué tan graves son y qué controles tienen sentido para reducirlos?**

El [NIST Cybersecurity Framework 2.0](https://www.nist.gov/publications/nist-cybersecurity-framework-csf-20) adopta precisamente una perspectiva basada en la gestión del riesgo y está diseñado para ayudar a organizaciones de distintos tamaños y niveles de madurez a entender, evaluar, priorizar y comunicar sus riesgos de ciberseguridad. ([NIST][1])

---

### Los cuatro conceptos que debemos distinguir

Una gran parte de la confusión al hablar de seguridad viene de utilizar como sinónimos términos que describen cosas diferentes.

#### Activo

Un **activo** es algo que nos importa proteger.

Puede ser:

* una cuenta;
* un computador;
* una aplicación;
* datos de clientes;
* código fuente;
* dinero;
* un servicio;
* la reputación de una organización.

No todos los activos tienen el mismo valor.

---

#### Amenaza

Una **amenaza** es una circunstancia, evento o actor con capacidad potencial de producir un impacto negativo.

Puede tratarse de:

* un atacante;
* malware;
* fraude;
* un empleado malicioso;
* un error humano;
* una vulnerabilidad explotada;
* un desastre que afecte la disponibilidad.

NIST define *threat* como una circunstancia o evento con potencial de afectar negativamente operaciones, activos o personas. ([NIST CSRC][2])

---

#### Vulnerabilidad

Una **vulnerabilidad** es una debilidad que puede ser explotada o activada por una amenaza.

Por ejemplo:

* software desactualizado;
* una contraseña reutilizada;
* permisos excesivos;
* una configuración incorrecta;
* una validación de entrada insuficiente.

NIST la describe como una debilidad en un sistema, sus procedimientos, controles internos o implementación que podría ser explotada o activada por una amenaza. ([NIST CSRC][3])

Una vulnerabilidad, por sí sola, **no equivale a un incidente**.

---

#### Riesgo

El **riesgo** representa la posibilidad de que una situación adversa ocurra y sus consecuencias.

Una forma sencilla de pensarlo es:

> **Riesgo ≈ probabilidad × impacto**

No debemos interpretar esto como una fórmula universal de cálculo. Es un modelo mental.

NIST define riesgo en términos de la medida en que una entidad está amenazada por una circunstancia o evento potencial, considerando normalmente tanto la probabilidad como el impacto adverso. ([NIST CSRC][4])

---

### Juntándolo todo

Podemos visualizarlo así:

```text
             ACTIVO
                │
                │ queremos proteger
                ▼
          ┌─────────────┐
          │   Amenaza   │
          └──────┬──────┘
                 │
                 │ aprovecha
                 ▼
          ┌─────────────┐
          │Vulnerabilidad│
          └──────┬──────┘
                 │
                 ▼
               RIESGO
                 │
                 │ puede producir
                 ▼
              IMPACTO
```

Pero en la práctica la relación es más compleja:

```text
        ¿Qué protegemos?
              ↓
            Activo
              ↓
        ¿Qué puede pasar?
              ↓
            Amenaza
              ↓
        ¿Cómo podría ocurrir?
              ↓
         Vulnerabilidad
              ↓
      ¿Qué consecuencias tendría?
              ↓
            Riesgo
```

Este razonamiento es la base de lo que posteriormente llamaremos **Threat Modeling**.

---

## Threat Modeling

**Threat Modeling** es un proceso estructurado para identificar y analizar amenazas contra un sistema, con el objetivo de tomar mejores decisiones de seguridad.

No necesitamos aprender una metodología específica todavía.

Para esta guía basta con adoptar cuatro preguntas:

> **¿Qué estamos protegiendo?**

> **¿De quién o de qué debemos protegerlo?**

> **¿Cómo podría producirse un incidente?**

> **¿Qué podemos hacer para reducir el riesgo?**

En capítulos posteriores aplicaremos este modelo a aplicaciones, APIs y sistemas de IA.

---

## La tríada CIA

Un modelo clásico para pensar sobre los objetivos de seguridad es la **CIA Triad**:

### Confidentiality — Confidencialidad

> **¿Quién puede acceder a la información?**

Un incidente de confidencialidad ocurre cuando información que debería estar restringida queda expuesta.

Ejemplo:

> Un atacante obtiene los datos personales de los clientes.

---

### Integrity — Integridad

> **¿Podemos confiar en que la información no fue modificada indebidamente?**

Ejemplo:

> Un atacante modifica una transacción antes de que sea procesada.

---

### Availability — Disponibilidad

> **¿Podemos acceder al sistema o información cuando los necesitamos?**

Ejemplo:

> Un ransomware cifra los archivos de un servidor y deja el servicio fuera de operación.

---

Estas propiedades están relacionadas, pero no son intercambiables.

Un sistema puede tener:

* buena confidencialidad pero mala disponibilidad;
* alta disponibilidad pero poca integridad;
* información íntegra pero completamente expuesta.

Por eso, cuando evaluamos un sistema, debemos preguntarnos **qué propiedades necesitamos proteger y qué consecuencias tendría perder cada una**.

---

# 2. Amenaza

Hasta ahora hemos hablado de conceptos abstractos. Veamos cómo se relacionan en un escenario real.

## El activo: una cuenta corporativa

Imaginemos una cuenta de correo corporativa.

Es un activo particularmente interesante porque puede contener:

* información interna;
* conversaciones con clientes;
* documentos;
* enlaces de recuperación;
* información sobre otros empleados;
* acceso a otros servicios.

### ¿Qué podría amenazarla?

Por ejemplo:

* phishing;
* credential stuffing;
* malware;
* robo de sesión;
* abuso interno.

### ¿Qué vulnerabilidades podrían facilitarlo?

* contraseña reutilizada;
* ausencia de MFA;
* permisos excesivos;
* dispositivo comprometido;
* mecanismos de recuperación débiles.

### ¿Qué podría ocurrir?

```text
Contraseña reutilizada
        ↓
Credencial comprometida
        ↓
Sin MFA
        ↓
Toma de control de la cuenta
        ↓
Acceso a información
        ↓
Uso de esa información para
nuevos ataques
```

Aquí aparece una idea importante:

> **Un incidente rara vez depende de una única vulnerabilidad.**

Los atacantes suelen encadenar condiciones.

Por eso la seguridad necesita **capas de protección**.

---

# 3. Ejemplo — Una cuenta comprometida

Supongamos que una persona utiliza la misma contraseña en varios servicios.

Uno de esos servicios sufre una filtración y la contraseña termina en manos de un atacante.

El atacante prueba esa combinación de usuario y contraseña contra el correo corporativo.

Si la cuenta no tiene MFA, puede conseguir acceso.

Una vez dentro, encuentra información sobre proyectos, clientes y compañeros de trabajo.

Ahora el atacante puede utilizar esa información para crear mensajes mucho más convincentes y dirigidos a otras personas.

El ataque evolucionó:

```text
        Credencial
            ↓
      Cuenta comprometida
            ↓
       Información
            ↓
    Ingeniería social
            ↓
     Nuevas víctimas
```

Lo importante no es memorizar este ataque concreto.

Lo importante es observar que **un pequeño fallo inicial puede convertirse en una cadena de compromisos**.

Por eso no basta con preguntar:

> "¿Tenemos antivirus?"

o:

> "¿Tenemos MFA?"

La pregunta correcta es:

> **"¿Qué ocurre si este control falla?"**

---

# 4. Control

Un **control de seguridad** es una medida utilizada para reducir un riesgo.

No existe un control que proteja contra todo.

Por eso utilizamos diferentes capas.

## Defense in Depth

**Defense in Depth** significa no depender de una única barrera de seguridad.

Por ejemplo:

```text
Contraseña
    +
MFA
    +
Seguridad del dispositivo
    +
Control de acceso
    +
Monitorización
    +
Recuperación
```

Si una capa falla, las demás pueden:

* impedir el ataque;
* limitar su alcance;
* detectarlo;
* facilitar la recuperación.

Esta idea será recurrente durante toda la guía.

---

## Least Privilege

**Least Privilege** significa proporcionar a una identidad, usuario, proceso o sistema **únicamente los permisos que necesita para realizar su función**.

Si una aplicación sólo necesita leer determinados datos, no debería tener permisos para modificar toda la base de datos.

Si un empleado sólo necesita acceso a un proyecto, no debería tener acceso a todos los proyectos.

Y si un agente de IA puede enviar correos, deberíamos preguntarnos:

> **¿Realmente necesita también poder eliminar archivos, modificar registros y ejecutar cualquier otra acción?**

Esta última pregunta será especialmente importante cuando lleguemos a los sistemas de IA.

---

## Assume Breach

**Assume Breach** propone diseñar sistemas asumiendo que, eventualmente, algún control será superado.

No significa asumir que todo está comprometido.

Significa preguntar:

> **"Si este componente fuese comprometido, ¿qué podría hacer el atacante?"**

Por ejemplo:

Si una cuenta corporativa fuese tomada:

* ¿qué información podría consultar?
* ¿qué otros sistemas podría alcanzar?
* ¿podría cambiar contraseñas?
* ¿podría acceder a información de clientes?
* ¿podría hacerse pasar por el usuario?

Esta mentalidad nos lleva naturalmente a:

* segmentación;
* least privilege;
* monitorización;
* límites de acceso;
* backups;
* recuperación.

---

## Los controles no sólo previenen

Una postura de seguridad madura no intenta únicamente **evitar** incidentes.

También intenta:

```text
PREVENIR
   ↓
DETECTAR
   ↓
RESPONDER
   ↓
RECUPERAR
```

### Prevenir

Reducir la probabilidad de que ocurra el incidente.

Ejemplos:

* MFA;
* cifrado;
* actualizaciones;
* control de acceso.

### Detectar

Identificar que algo está ocurriendo.

Ejemplos:

* logs;
* alertas;
* monitorización.

### Responder

Contener y controlar el incidente.

### Recuperar

Restaurar las operaciones y reducir el impacto residual.

Los dos últimos conceptos tendrán su propio capítulo más adelante.

---

# 5. El lente de la IA

Hasta aquí hemos hablado de principios que existían mucho antes de los modelos generativos.

Entonces, ¿qué cambia?

La respuesta corta es:

> **La IA no reemplaza estos fundamentos. Cambia las capacidades disponibles para atacantes y defensores, introduce nuevas superficies de ataque y puede invalidar algunas de nuestras suposiciones sobre el riesgo.**

Podemos pensar en cuatro efectos.

---

## IA como amplificador

Una capacidad que ya existía puede hacerse:

* más rápida;
* más barata;
* más escalable;
* más personalizada.

Por ejemplo, una campaña de ingeniería social puede requerir investigación, redacción y traducción.

La IA puede automatizar parte de ese trabajo.

El ataque fundamental no cambió.

**Su economía sí.**

---

## IA como nueva superficie

Al introducir IA en una aplicación también introducimos nuevos componentes:

```text
Aplicación
    ↓
Modelo
    ↓
Prompts
    ↓
Datos
    ↓
RAG
    ↓
Tools / APIs
```

Cada componente puede introducir nuevos riesgos.

Por ejemplo:

* prompt injection;
* exposición de información;
* acceso indebido a datos;
* abuso de herramientas;
* comportamiento inesperado de agentes.

Estos temas serán el centro del capítulo de **Seguridad de sistemas de IA**.

---

## IA como herramienta

La IA no pertenece exclusivamente al atacante.

Puede utilizarse para:

### Atacar

* reconocimiento;
* generación de contenido;
* automatización;
* análisis de código;
* ingeniería social.

### Defender

* análisis de logs;
* detección;
* generación de reglas;
* análisis de vulnerabilidades;
* asistencia en respuesta.

### Desarrollar

* generación de código;
* testing;
* documentación;
* revisión.

Por eso:

> **IA no es sinónimo de amenaza. Es una capacidad que puede modificar el equilibrio entre atacantes y defensores.**

---

## IA como cambio del threat model

Este es el cambio más profundo.

Un **threat model** depende de nuestras suposiciones sobre:

* quién puede atacarnos;
* qué capacidades tiene;
* qué información posee;
* qué acciones puede realizar;
* cuánto le cuesta realizar un ataque.

La IA puede cambiar esas suposiciones.

Por ejemplo:

### Antes

> "Un atacante no puede personalizar un mensaje para cada empleado."

### Ahora

La personalización puede automatizarse a gran escala.

---

### Antes

> "Una llamada de una persona conocida es una señal razonable de identidad."

### Ahora

La clonación de voz reduce el valor de esa señal.

---

### Antes

> "Un programa sólo puede realizar las acciones que explícitamente programamos."

### Ahora

Un agente puede interpretar objetivos y utilizar herramientas para actuar sobre sistemas externos.

Esto no significa que todos estos ataques sean triviales.

Significa que **las suposiciones que utilizamos para evaluar el riesgo deben revisarse**.

---

# 6. Takeaways

Si sólo recuerdas seis cosas de este capítulo:

1. **Seguridad comienza por identificar qué estamos protegiendo.**

2. **Amenaza, vulnerabilidad y riesgo son conceptos diferentes.**

3. **El riesgo depende tanto de la probabilidad como del impacto.**

4. **Defense in Depth y Least Privilege limitan el daño cuando un control falla.**

5. **Assume Breach nos obliga a pensar en las consecuencias de un compromiso, no sólo en cómo evitarlo.**

6. **La IA no reemplaza los fundamentos de seguridad: cambia el threat model.**

---

# 7. Fuentes

* [NIST Cybersecurity Framework (CSF) 2.0](https://www.nist.gov/publications/nist-cybersecurity-framework-csf-20?utm_source=chatgpt.com) — marco de referencia para gestionar y comunicar riesgos de ciberseguridad.
* [NIST Cybersecurity Framework Resource & Overview Guide](https://www.nist.gov/publications/nist-cybersecurity-framework-20-resource-overview-guide?utm_source=chatgpt.com) — introducción práctica al CSF 2.0.
* [NIST Cybersecurity Glossary](https://csrc.nist.gov/glossary?utm_source=chatgpt.com) — terminología y definiciones de ciberseguridad.
* [NIST — Threat](https://csrc.nist.gov/glossary/term/threat?utm_source=chatgpt.com) — definición de *threat*.
* [NIST — Vulnerability](https://csrc.nist.gov/glossary/term/vulnerability?utm_source=chatgpt.com) — definición de *vulnerability*.
* [NIST — Risk](https://csrc.nist.gov/glossary/term/risk?utm_source=chatgpt.com) — definición de *risk*.

---

### Nota editorial

Este primer borrador deliberadamente **no intenta enseñar todo lo que podría caber en un capítulo introductorio**. Su trabajo es instalar un modelo mental que podamos reutilizar.

En particular, dejaría como regla para las siguientes iteraciones que:

> **Si un concepto aparece aquí pero se desarrolla en otro capítulo, aquí sólo enseñamos lo necesario para que el lector pueda reconocerlo.**

Eso aplica a *Threat Modeling*, Least Privilege, Assume Breach, controles detectivos, etc.

También mantendría **el ejemplo de la cuenta comprometida** como candidato fuerte para convertirse en un ejemplo recurrente de la presentación. Nos permite demostrar, sin cambiar de escenario, cómo los distintos capítulos van agregando capas de protección.

[1]: https://www.nist.gov/publications/nist-cybersecurity-framework-csf-20?utm_source=chatgpt.com "The NIST Cybersecurity Framework (CSF) 2.0 | NIST"
[2]: https://csrc.nist.gov/glossary/term/threat?utm_source=chatgpt.com "threat - Glossary | CSRC"
[3]: https://csrc.nist.gov/glossary/term/vulnerability?utm_source=chatgpt.com "vulnerability - Glossary | CSRC"
[4]: https://csrc.nist.gov/glossary/term/risk?utm_source=chatgpt.com "risk - Glossary | CSRC"

