# to-dos-prod-env

This repo's purpose is deployment of to-dos product's shared resources to Production cluster. In this case the shared resources for [to-dos-ui](https://github.com/TourmalineCore/to-dos-ui) and [to-dos-api](https://github.com/TourmalineCore/to-dos-api) are nginx and https.

Deployment happens only from a pipeline. It isn't happining locally as for [to-dos-local-env](https://github.com/TourmalineCore/to-dos-local-env) use case.

Here locally you can only look at the final helmfile to be applied from the pipeline.

More info about the project and its related repos can be found here: [to-dos-documentation](https://github.com/TourmalineCore/to-dos-documentation).

## Prerequisites

1. Install Docker
2. Install Visual Studio Code
3. Install Visual Studio Code [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) Extension

## VSCode Dev Container

Open this repo's folder in VSCode, it might immediately propose you to re-open it in a Dev Container or you can click on `Remote Explorer`, find plus button and choose the `Open Current Folder in Container` option and wait when it is ready.

When your Dev Container is ready, the VS Code window will be re-opened. Open a new terminal in this Dev Container which will be executing the commands under this prepared Linux container where we have already pre-installed and pre-configured:
- Docker Outside of Docker aka Docker from Docker to be able to use host's docker daemon from inside the container 
- [helm, helmfile](https://github.com/helmfile/helmfile) to deploy all services [helm](https://helm.sh/) charts at once to the local k8s cluster created with `kind`
- [helm-diff](https://github.com/databus23/helm-diff) show nicely what has changed since the last `helmfile apply`

>Note: You **don't** need to install these packages in your OS, these are part of the Dev Container already. Thus, it is a clean way to run the stack for any host OS.

### Debugging Helm Charts

To see how all charts manifest are going to look like before apply you can execute the following command:

```bash
helmfile --namespace prod -f deploy/helmfile.yaml template
```
