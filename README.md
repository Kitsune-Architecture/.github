# .github

Repo especial de la organización **Kitsune-Architecture**. Contiene:

- `profile/README.md` — portada de la organización (se muestra en la página principal).
- `.github/workflows/` — workflows reutilizables (Dart CI, Flutter CI).
- `ISSUE_TEMPLATE/spec-change.yml` — plantilla de issue por defecto para toda la org.

## Invocar los workflows reutilizables desde otro repo

GitHub exige que un *reusable workflow* viva bajo `.github/workflows/` sin importar el nombre
del repo que lo aloja. Como este repo se llama `.github`, la ruta queda anidada dos veces:

```yaml
# ej. en kitsune-tools/.github/workflows/ci.yml
jobs:
  ci:
    uses: Kitsune-Architecture/.github/.github/workflows/dart-ci.yml@main
    with:
      working-directory: dart/kitsune_generator
```

```yaml
# ej. en kitsune-examples/.github/workflows/ci.yml (por cada ejemplo)
jobs:
  ci:
    uses: Kitsune-Architecture/.github/.github/workflows/flutter-ci.yml@main
    with:
      working-directory: flutter/kitsune_hello_flow
```

No es un error de tipeo: `.github/.github/workflows/...` es la ruta correcta.
