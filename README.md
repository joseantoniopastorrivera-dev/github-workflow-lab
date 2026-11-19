# github-workflow-lab

Laboratorio para practicar el flujo de trabajo de GitHub: ramas, issues, pull requests y merges, usando `git` y la CLI `gh`.

## Qué hay aquí

- `README.md`: este archivo.
- `LICENSE`: licencia MIT.
- `.gitignore`: archivos que no se suben.

## Flujo de trabajo

1. Crear una rama desde `main` con un nombre que diga qué hace: `docs/...`, `ci/...`, `feat/...`.
2. Hacer commits pequeños con mensajes en español (`tipo: qué cambia`).
3. Subir la rama y abrir una pull request con `gh pr create`.
4. Revisar el diff y mergear con `gh pr merge`.
5. Borrar la rama y volver a `main` con `git pull`.

## Estado

En construcción: cada cambio entra por una rama y una pull request.
