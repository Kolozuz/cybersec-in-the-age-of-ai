# Capítulo 0 — Contexto y modelos mentales

> **Antes de aprender herramientas, aprende a pensar en términos de riesgo.**

La ciberseguridad no consiste en eliminar todos los riesgos. Eso no es posible.

Consiste en **identificar qué queremos proteger, entender qué podría salir mal y aplicar controles que reduzcan la probabilidad o el impacto de esos escenarios**.

Este modelo de pensamiento será el hilo conductor del resto de la guía.

---

# 1. Concepto

## ¿Qué es ciberseguridad?

Podemos entender la ciberseguridad como la disciplina de **proteger sistemas, datos, servicios y personas frente a amenazas digitales, reduciendo la probabilidad y el impacto de incidentes**.

La pregunta importante no es:

> "¿Cómo elimino todos los riesgos?"

Sino:

> **"¿Qué riesgos importan y qué puedo hacer para reducirlos?"**

Esta perspectiva basada en riesgo es también la adoptada por marcos de referencia como el **NIST Cybersecurity Framework (CSF) 2.0**.

---

## Activo

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

Perder una presentación interna y perder la base de datos de clientes pueden ser incidentes muy diferentes, aunque ambos impliquen "pérdida de información".

---

## Amenaza

Una **amenaza** es una circunstancia, evento o actor con capacidad potencial de producir un impacto negativo.

Puede tratarse de:

* un atacante;
* malware;
* fraude;
* un empleado malicioso;
* un error humano;
* un desastre físico.

Una amenaza describe **qué podría causar daño**.

---

## Vulnerabilidad

Una **vulnerabilidad** es una debilidad que puede ser explotada o activada por una amenaza.

Por ejemplo:

* software desactualizado;
* una contraseña reutilizada;
* permisos excesivos;
* una configuración incorrecta;
* una validación de entrada insuficiente.

Una vulnerabilidad no significa necesariamente que haya ocurrido un incidente.

Es una **condición que puede facilitarlo**.

---

## Riesgo

El **riesgo** representa la posibilidad de que una situación adversa ocurra y sus consecuencias.

Una forma sencilla de pensarlo es:

> **Riesgo ≈ probabilidad × impacto**

No debemos interpretar esto como una fórmula universal de cálculo. Es un modelo mental.

Un evento poco probable puede seguir siendo un riesgo importante si su impacto potencial es enorme. Del mismo modo, un evento frecuente puede merecer atención incluso si cada ocurrencia individual tiene un impacto relativamente pequeño.

---

## De activo a riesgo

Podemos juntar los conceptos:

```text
¿Qué queremos proteger?
          ↓
        ACTIVO
          ↓
¿Qué podría causarle daño?
          ↓
       AMENAZA
          ↓
¿Cómo podría ocurrir?
          ↓
    VULNERABILIDAD
          ↓
¿Qué consecuencias tendría?
          ↓
        RIESGO
```

Esta forma de pensar nos lleva a una pregunta fundamental:

> **¿Qué tendría que ocurrir para que este activo se vea comprometido?**

---

## Threat Modeling

**Threat Modeling** es un proceso estructurado para identificar y analizar amenazas contra un sistema con el objetivo de tomar mejores decisiones de seguridad.

No necesitamos aprender una metodología específica todavía.

Para esta guía basta con adoptar cuatro preguntas:

> **¿Qué estamos protegiendo?**

> **¿De quién o de qué debemos protegerlo?**

> **¿Cómo podría producirse un incidente?**

> **¿Qué podemos hacer para reducir el riesgo?**

Este razonamiento puede aplicarse tanto a una cuenta personal como a una aplicación empresarial o a un sistema de IA.

Más adelante utilizaremos Threat Modeling de forma más concreta en el desarrollo seguro.

---

# La tríada CIA

Un modelo clásico para pensar sobre los objetivos de seguridad es la **CIA Triad**.

| Propiedad           | Pregunta                                 | Ejemplo de incidente                              |
| ------------------- | ---------------------------------------- | ------------------------------------------------- |
| **Confidentiality** | ¿Quién puede verlo?                      | Se filtran datos de clientes                      |
| **Integrity**       | ¿Podemos confiar en que no fue alterado? | Se modifica una transacción                       |
| **Availability**    | ¿Podemos acceder cuando lo necesitamos?  | Un ransomware deja un servicio fuera de operación |

Estas propiedades están relacionadas, pero no son intercambiables.

Un sistema puede tener buena confidencialidad pero mala disponibilidad. O puede estar disponible para todos mientras su integridad está comprometida.

Por eso, al evaluar un sistema debemos preguntarnos:

> **¿Qué propiedades necesitamos proteger y qué consecuencias tendría perder cada una?**

---

# 2. Amenaza

Un mismo activo puede tener múltiples caminos de ataque.

Consideremos una cuenta corporativa.

### Activo

Una cuenta de correo electrónico.

Puede contener:

* información interna;
* conversaciones con clientes;
* documentos;
* enlaces de recuperación;
* información sobre otros empleados.

### Amenazas

Por ejemplo:

* phishing;
* credential stuffing;
* malware;
* robo de sesión;
* abuso interno.

### Vulnerabilidades

Por ejemplo:

* contraseña reutilizada;
* ausencia de MFA;
* permisos excesivos;
* dispositivo comprometido;
* mecanismos de recuperación débiles.

Esto nos lleva a una idea importante:

> **Un incidente rara vez depende de una única vulnerabilidad.**

Los atacantes pueden encadenar condiciones aparentemente independientes.

Por eso la seguridad necesita **capas de protección**.

---

# 3. Ejemplo — Una cuenta comprometida

Supongamos que una persona utiliza la misma contraseña en varios servicios.

Uno de esos servicios sufre una filtración y la contraseña termina en manos de un atacante.

El atacante prueba esa combinación contra el correo corporativo.

La cuenta no tiene MFA.

El atacante consigue acceso.

Dentro del correo encuentra información sobre proyectos, clientes y compañeros de trabajo.

Ahora puede utilizar esa información para crear mensajes mucho más convincentes y dirigidos a otras personas.

El ataque evolucionó:

```text
Contraseña reutilizada
          ↓
Credencial comprometida
          ↓
       Sin MFA
          ↓
Toma de control de cuenta
          ↓
Acceso a información
          ↓
Ingeniería social
          ↓
   Nuevas víctimas
```

El objetivo del ejemplo no es memorizar un ataque concreto.

Es observar cómo:

> **un fallo inicial puede convertirse en una cadena de compromisos.**

Este mismo escenario reaparecerá en distintos puntos de la guía para mostrar cómo diferentes controles pueden romper esa cadena.

---

# 4. Control

Un **control de seguridad** es una medida utilizada para reducir un riesgo.

Aquí conviene establecer una distinción:

> **Un control no es necesariamente una herramienta.**

Por ejemplo:

* **MFA** es un control.
* Un **password manager** es una herramienta que facilita determinadas prácticas de seguridad.
* Una **VPN** es una herramienta que resuelve problemas específicos de comunicación y privacidad.

La pregunta correcta no es:

> "¿Qué herramienta necesito?"

Sino:

> **"¿Qué riesgo quiero reducir y qué control es apropiado?"**

---

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

La seguridad efectiva suele depender de **varios controles complementarios**, no de una herramienta milagrosa.

---

## Least Privilege

**Least Privilege** significa proporcionar a una identidad, usuario, proceso o sistema **únicamente los permisos que necesita para realizar su función**.

Si una aplicación sólo necesita leer determinados datos, no debería tener permisos para modificar toda la base de datos.

Si un empleado sólo necesita acceso a un proyecto, no debería tener acceso a todos los proyectos.

Y si un agente de IA puede enviar correos, deberíamos preguntarnos:

> **¿Realmente necesita también poder eliminar archivos, modificar registros y ejecutar otras acciones?**

Esta última pregunta será especialmente importante cuando lleguemos a los sistemas de IA.

---

## Assume Breach

**Assume Breach** propone diseñar sistemas asumiendo que, eventualmente, algún control será superado.

No significa asumir que todo está comprometido.

Significa preguntar:

> **"Si este componente fuese comprometido, ¿qué podría hacer el atacante?"**

Por ejemplo, si una cuenta corporativa fuese tomada:

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

Los dos últimos conceptos tendrán un tratamiento más profundo en el capítulo de **Resiliencia y respuesta**.

---

# 5. El lente de la IA

La IA no reemplaza estos fundamentos.

**Cambia las capacidades disponibles para atacantes y defensores, introduce nuevas superficies de ataque y puede invalidar algunas de nuestras suposiciones sobre el riesgo.**

Para cada concepto de la guía podemos hacernos cuatro preguntas.

---

## 1. ¿Qué capacidades existentes amplifica?

Una actividad que ya existía puede hacerse:

* más rápida;
* más barata;
* más escalable;
* más personalizada.

Por ejemplo, una campaña de ingeniería social requiere investigar a las víctimas y crear mensajes convincentes.

La IA puede automatizar parte de ese trabajo.

El ataque fundamental no cambió.

**Su economía sí.**

---

## 2. ¿Qué nuevas superficies introduce?

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

Cada componente puede introducir nuevos riesgos:

* prompt injection;
* exposición de información;
* acceso indebido a datos;
* abuso de herramientas;
* comportamiento inesperado de agentes.

Estos temas serán el centro del capítulo de **Seguridad de sistemas de IA**.

---

## 3. ¿Cómo cambia las capacidades del atacante y del defensor?

La IA puede utilizarse para:

**Atacar**

* reconocimiento;
* generación de contenido;
* automatización;
* análisis de código;
* ingeniería social.

**Defender**

* análisis de logs;
* detección;
* análisis de vulnerabilidades;
* generación de reglas;
* asistencia en respuesta.

**Desarrollar**

* generación de código;
* testing;
* documentación;
* revisión.

Por eso:

> **IA no es sinónimo de amenaza. Es una capacidad que puede modificar el equilibrio entre atacantes y defensores.**

---

## 4. ¿Qué supuestos de nuestro Threat Model dejan de ser válidos?

Este puede ser el cambio más profundo.

Un Threat Model depende de nuestras suposiciones sobre:

* quién puede atacarnos;
* qué capacidades tiene;
* qué información posee;
* qué acciones puede realizar;
* cuánto le cuesta realizar un ataque.

La IA puede cambiar esas suposiciones.

### Antes

> "Un atacante no puede personalizar un mensaje para cada empleado."

### Ahora

La personalización puede automatizarse a gran escala.

---

### Antes

> "Una llamada de una persona conocida es una señal razonable de identidad."

### Ahora

La clonación de voz puede reducir el valor de esa señal.

---

### Antes

> "Una aplicación sólo puede realizar las acciones que programamos explícitamente."

### Ahora

Un agente puede interpretar objetivos y utilizar herramientas para actuar sobre sistemas externos.

Esto no significa que estos ataques sean triviales.

Significa que:

> **Cuando cambian las capacidades disponibles, debemos revisar nuestro Threat Model.**

---

# 6. Takeaways

> ### La seguridad no consiste en encontrar la herramienta correcta.
>
> ### Consiste en entender el riesgo y aplicar las capas de control adecuadas.

Si sólo recuerdas cinco cosas de este capítulo:

1. **Identifica qué estás protegiendo.**
2. **Distingue amenazas, vulnerabilidades y riesgos.**
3. **Utiliza múltiples capas de control: ningún control es perfecto.**
4. **Asume que algún control eventualmente puede fallar y limita el impacto de ese fallo.**
5. **Cuando cambia la tecnología, revisa tu Threat Model. La IA es un ejemplo especialmente importante.**

---

# 7. Fuentes

* [NIST Cybersecurity Framework (CSF) 2.0](https://www.nist.gov/publications/nist-cybersecurity-framework-csf-20) — marco de referencia para gestionar y comunicar riesgos de ciberseguridad.
* [NIST Cybersecurity Framework 2.0: Resource & Overview Guide](https://www.nist.gov/publications/nist-cybersecurity-framework-20-resource-overview-guide) — introducción al CSF 2.0 y sus conceptos principales.
* [NIST Cybersecurity Glossary](https://csrc.nist.gov/glossary) — terminología de ciberseguridad.
* [NIST — Threat](https://csrc.nist.gov/glossary/term/threat) — definición de *threat*.
* [NIST — Vulnerability](https://csrc.nist.gov/glossary/term/vulnerability) — definición de *vulnerability*.
* [NIST — Risk](https://csrc.nist.gov/glossary/term/risk) — definición de *risk*.
