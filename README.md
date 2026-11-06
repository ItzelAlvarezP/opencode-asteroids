# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Descripción

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye power-ups especiales, un OVNI enemigo que dispara y tipos de asteroides únicos como la estrella fugaz.

## Tecnologías

- **HTML5 Canvas** — renderizado 2D
- **JavaScript (ES6+)** — lógica del juego en un solo archivo `game.js`
- Sin frameworks, sin bundler, sin dependencias

## Cómo correr

Abre `index.html` directamente en el navegador (doble clic), o usa un servidor local:

```bash
npx serve .
```

Luego visita `http://localhost:3000`.

## Controles

| Tecla     | Acción               |
| --------- | -------------------- |
| `←` `→`   | Rotar nave           |
| `↑`       | Propulsar            |
| `Espacio` | Disparar             |
| `C`       | Cambiar apariencia   |

El power-up **Velocidad** (círculo celeste con «V») aparece aleatoriamente. Recógelo con la nave para duplicar la propulsión durante 5 segundos; el tiempo restante se muestra en pantalla.

El power-up **Escudo** (círculo verde con «E») otorga 6 segundos de protección: los proyectiles del OVNI se destruyen al impactar contra el anillo de la nave. El escudo no protege de los asteroides.

El **OVNI enemigo** aparece periódicamente y dispara proyectiles rojos apuntando a la nave. Puedes destruirlo con tus disparos para sumar puntos.

La **estrella fugaz** es un asteroide especial más rápido que lo normal, con un rastro dorado. Desaparece tras unos segundos si no la destruyes.

## Puntuación

| Asteroide | Puntos |
| --------- | ------ |
| Grande    | 20     |
| Mediano   | 50     |
| Pequeño   | 100    |
| Estrella fugaz | 100 |
| OVNI      | 150    |

## Características

- 3 vidas con invencibilidad temporal al reaparecer (parpadeo)
- Asteroides se parten en fragmentos más pequeños al ser destruidos
- Power-ups de velocidad y escudo temporal
- OVNI enemigo que dispara proyectiles apuntando a la nave
- Partículas de explosión al destruir asteroides
- 4 apariencias de nave intercambiables con `C`
