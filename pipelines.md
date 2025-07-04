# Configuración de Pipelines y Revisión de Pull Requests

Para mantener la calidad del código y una integración continua efectiva, es fundamental agregar y configurar los pipelines (workflows) en los repositorios en los que estamos trabajando.

## 1. Agregar Workflows en .github/workflows

Dentro de la carpeta `.github/workflows` de tu repositorio, crea los archivos YAML necesarios para automatizar la ejecución de linters y validar los Pull Requests.

### Pipeline para ESLint
Este pipeline ejecuta ESLint automáticamente en cada push, ayudando a mantener un código limpio y consistente. el pnpm es una referencia debe ajustarse a cada proyecto ya sea con yarn o npm

``` yml
name: ESLint
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install pnpm
        uses: pnpm/action-setup@v2
        with:
          version: 8 # Puedes ajustar la versión si necesitas otra
      - name: Install modules
        run: pnpm install
      - name: Run ESLint
        run: pnpm lint
```

> 💡 Recomendación: Asegúrate de tener configurado el script lint en tu package.json. y cambiar pnpm por lo que se ocupe en el proyecto

### Pipeline para Validar Pull Requests (PR)
Este pipeline verifica que los títulos de los Pull Requests sigan el [formato semántico](https://www.conventionalcommits.org/en/v1.0.0/) recomendado, ayudando a automatizar el versionado y mantener buenas prácticas en la gestión de PRs.

``` yml
name: "Lint PR"

on:
  pull_request_target:
    types:
      - opened
      - edited
      - synchronize
      - reopened

jobs:
  main:
    name: Validate PR title
    runs-on: ubuntu-latest
    permissions:
      pull-requests: read
    steps:
      - uses: amannn/action-semantic-pull-request@v5
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```



## 2. Configuración de Pull Requests en GitHub

Es importante ajustar los settings del repositorio para reforzar la revisión y aprobación de los Pull Requests:

* Ve a Settings > General.
* En la sección de Pull Requests, configura las políticas de revisión según las necesidades del equipo:

    - Solicitar que los branches estén actualizados antes de permitir el merge.

    - Activar la opción para evitar merges si el PR no pasa los checks configurados (como los workflows anteriores).

Puedes ver un ejemplo de configuración en la siguiente imagen:

<img src="config-pr.png" alt="Configuración de Pull Request" width="600"/>

