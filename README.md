# bmlabs-central-workflows

## Configuracion de secretos 

Se deben configurar los siguiente secretos, en el repositorio a revisar, esto se hace en el menu de repositorio Setting -> Secrets & Variables -> Action

```code
  OPENAI_API_KEY
  REGISTRY_SECRET
  BUCKET
  BUCKET_ACCESS_KEY
  BUCKET_SECRET_KEY
```
## Instalación de la herramienta `gh`

La herramienta [`gh`](https://cli.github.com/) es la CLI oficial de GitHub. Para instalarla en macOS, ejecuta:

```sh
brew install gh
```

Verifica la instalación con:

```sh
gh --version
```

## Ejecución del Action `smith`

### 1. Copiar el archivo `smith.yaml`

Copia el archivo `smith.yaml` desde la raíz de este repositorio al directorio .github/workflows de tu repositorio

```sh
cp /ruta/al/bmlabs-central-workflows/smith.yaml /ruta/al/tu-proyecto/.github/workflows
```

### 2. Ejecutar el Action

Utiliza la herramienta `gh` para ejecutar el action. Asegúrate de estar autenticado con GitHub (`gh auth login`).

Ejemplo de ejecución:

```sh
 gh workflow run run-smith.yaml --ref develop
```

No olvides configurar el agente para que pueda revisar tu repo, abre el archivo smith.yaml y modifica los siguentes paraemtros 

    PROJECT_KEY: Nombre del proyecto o repositorio
    FRAMEWORK: framework usado
    LENGUAJE: lenguaje
    EXTENSION: extension de los archivos que contienen codigo, sin el punto, ejemplo para netcore la extension de los archivos es  cs  
    BRANCH: Rama donde este el codigo

Ejemplo: para una aplicacion .netcore
```code
      PROJECT_KEY: bmlabs-votacion-api
      FRAMEWORK: net core
      LENGUAJE: C#
      EXTENSION: cs      
      BRANCH: dev
```

Ejemplo: para una aplicacion vuejs
```code
      PROJECT_KEY: bmlabs-votacion-app
      FRAMEWORK: vuejs
      LENGUAJE: javascript
      EXTENSION: js      
      BRANCH: dev
```



### 3. Revisión del log de ejecución

Para revisar el log de ejecución del workflow:

1. Obtén la lista de ejecuciones:
   ```sh
   gh run list --repo <owner>/<repo>
   ```
2. Visualiza el log de una ejecución específica:
   ```sh
   gh run view <run-id> --repo <owner>/<repo> --log
   ```

Reemplaza `<run-id>` por el ID de la ejecución que deseas revisar.

---

Para más información sobre `gh` y workflows de GitHub Actions, consulta la [documentación oficial](https://cli.github.com/manual/).
