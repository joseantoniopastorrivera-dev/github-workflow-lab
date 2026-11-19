# Chuleta de git y gh

Comandos usados en este laboratorio, en el orden en que aparecen en el flujo de trabajo.

## Crear el repositorio

```powershell
git init -b main
git add .
git commit -m "chore: estructura inicial"
gh repo create github-workflow-lab --public --source . --push
```

`--source .` usa la carpeta actual y `--push` sube `main` en el mismo paso.

## Issues

```powershell
gh issue create --title "Título" --body "Descripción"
gh issue close 1 --reason completed --comment "Hecho"
gh issue list --state all
```

## Ramas y pull requests

```powershell
git switch -c docs/mi-cambio          # crea la rama y se cambia a ella
git add README.md
git commit -m "docs: qué cambia"
git push -u origin docs/mi-cambio     # -u enlaza la rama local con la remota
gh pr create --base main --title "docs: qué cambia" --body "Por qué"
gh pr checks 3 --watch                # espera a la CI
gh pr merge 3 --merge --delete-branch # merge commit y borra la rama remota
git switch main
git pull
```

## Commits con coautor

Se añade una línea `Co-authored-by` al final del mensaje, separada por una línea en blanco:

```text
docs: añade la chuleta de git y gh

Co-authored-by: Nombre <id+usuario@users.noreply.github.com>
```

El email debe ser uno que GitHub asocie a la cuenta del coautor. El noreply se obtiene con `gh api users/<usuario> --jq .id`.

## Cuando falla la CI

1. `gh pr checks <n>` para ver qué job falla.
2. `gh run view <id> --log-failed` para leer el error.
3. Se corrige en la misma rama, se hace commit y push, y la PR se actualiza sola.
