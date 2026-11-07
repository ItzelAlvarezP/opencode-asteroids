---
name: Create Issue
description: Formatea y publica issues de GitHub en este repo — conserva el texto del usuario verbatim, añade contexto de código relevante y aplica labels de tipo + área.
---

# Crear un issue en este repo

Úsalo cada vez que el usuario pida crear un issue en `ItzelAlvarezP/opencode-asteroids`.

## Reglas invariables

- El texto de la persona se publica **verbatim**: sin corregir, traducir, resumir ni parafrasear. Va en su propia sección, claramente marcada.
- Lo que el agente aporta no se mezcla con el texto original: vive en la sección `## Contexto del código`.
- No publicar sin que el usuario confirme título y body.

## Workflow

1. Recoge lo que la persona quiere reportar; pregunta solo lo que falte para entender el problema.
2. Busca en el código los archivos y símbolos relacionados (`grep`, `read`) y anota por qué son relevantes para quien revise el issue.
3. Redacta el issue con el formato estándar y elige labels (ver abajo).
4. Muestra título y body completos y pide confirmación.
5. Publica y reporta la URL.

## Formato estándar

```markdown
## Resumen

<!-- 1–2 frases que describan el problema o pedido. -->

## Contexto del código

<!-- Aportado por el agente: rutas e identificadores concretos, por ejemplo: -->
<!-- - `game.js` — `wrap()`: el mundo es toroidal, el síntoma puede venir del wrapping. -->

## Reporte original

> <!-- Texto de la persona EXACTAMENTE como lo escribió, cada línea con prefijo `>`. -->
```

Título: `<área>: <fallo o pedido>` — corto y buscable.
Ejemplos: `powerup: escudo no caduca tras 6s`, `enemy: láser apunta por el borde toroidal`.

## Labels

Elige según el contenido (1–2 labels):

- Tipo: `bug` | `enhancement` | `question` | `docs`
- Área: `game` | `ui` | `asteroid` | `powerup` | `enemy` | `physics` | `perf`

Verifica primero con `gh label list`. Si el label elegido no existe, pregunta al usuario si crearlo (`gh label create <name>`) u omitirlo; nunca lo adivines ni lo inventes.

## Publicación

```sh
gh issue create --title "<title>" --body-file <file>
```

- Escribe el body en un archivo temporal previo para preservar saltos de línea, code fences y comillas.
- Añade labels con `--label a,b`.
- Si `gh` no está instalado o autenticado, entrega el título y body listos para copiar y explica el bloqueo.

Tras publicar, reporta la URL del issue.
