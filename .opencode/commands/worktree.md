---
description: Crea un git worktree en .worktrees/<nombre>
agent: build
---

Crea un worktree para: $ARGUMENTS

Reglas:
- Normaliza el argumento a un nombre válido de rama: minúsculas, espacios → `-`, sin acentos ni caracteres especiales.
- Si el argumento queda vacío, pide un nombre y detente.
- Ejecuta únicamente: `git worktree add .worktrees/<nombre>`
- No cambies de directorio, no leas/escribas archivos, no ejecutes otros comandos.
- Responde solo con la ruta y la rama creadas.
