## Formato estandar de cada capitulo

```md
# Título

## 1. Concepto
¿Qué es y por qué importa?

## 2. Amenaza
¿Qué puede salir mal?
¿Cómo podría aprovecharlo un atacante?

## 3. Ejemplo
Un caso concreto que haga tangible el riesgo.

## 4. Control
¿Qué podemos hacer para reducir el riesgo?

## 5. El lente de la IA
¿Qué cambia cuando introducimos IA?
¿Qué nuevas amenazas aparecen?
¿Qué controles debemos adaptar?

## 6. Takeaways
3–5 ideas que el lector debería recordar.

## 7. Fuentes
Fuentes primarias y referencias confiables.
```

## Convenciones sobre duración

Por ejemplo en Contraseñas podríamos tener:

Concepto — 1 slide
Amenaza — 1–2 slides
Ejemplo — 1 slide
Control — 2 slides
IA — 1 slide
Takeaways — 1 slide

Mientras que en Resiliencia y respuesta probablemente:

Concepto — breve
Amenaza — breve
Ejemplo — breve
Control — 1–2 slides
IA — breve
Takeaways — 1 slide

La plantilla es estructural, no una camisa de fuerza.

## Convenciones sobre ejemplos

Los ejemplos deberían ser concretos y reconocibles, pero no convertirse en tutoriales ofensivos.

Preferiría:

"Un atacante obtiene información pública de un empleado, genera un correo convincente imitando el estilo de su jefe y solicita una acción urgente."

sobre:

una explicación paso a paso de cómo construir ese ataque.

Esto es especialmente importante en los capítulos de phishing, malware y seguridad de IA.

## Convenciones sobre "El lente de la IA"

En cada capítulo deberíamos intentar responder explícitamente:

¿Qué cambia cuando introducimos IA?

Pero la respuesta no tiene que ser siempre "apareció una vulnerabilidad nueva".

Podemos clasificar el efecto de IA en cuatro categorías:

1. Amplificador

La IA hace algo que ya existía más rápido, barato o escalable.

Ejemplo: phishing.

2. Nueva superficie

La IA introduce un componente nuevo que debemos proteger.

Ejemplo: prompt injection.

3. Nueva herramienta

La IA cambia cómo los defensores o atacantes realizan su trabajo.

Ejemplo: AI-assisted code review.

4. Cambio de threat model

La IA altera las suposiciones que utilizábamos para evaluar el riesgo.

Ejemplo: confiar en que una llamada de voz es evidencia suficiente de identidad.

Esto nos permite evitar el error de intentar meter "IA" artificialmente en cada capítulo.

## Convenciones sobre fuentes

La sección Fuentes no será simplemente una bibliografía acumulativa.

Intentaría distinguir:

Fuente primaria

OWASP
NIST
CISA
RFCs
documentación oficial de fabricantes/proveedores
papers académicos cuando corresponda

Fuente secundaria

investigaciones de organizaciones reconocidas
reportes de seguridad de proveedores
publicaciones técnicas de reputación comprobada

Y cuando una afirmación importante dependa de una fuente concreta, procuraremos que quede asociada al concepto correspondiente, no enterrada al final de una lista enorme.

Esto será especialmente importante en Seguridad de sistemas de IA, donde el panorama evoluciona rápido.
