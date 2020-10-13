# Tekton explored

### What is tekton ?

Tekton is a powerful and flexible **open-source framework for creating CI/CD systems** , allowing developers to **build, test, and deploy** across cloud providers and on-premise systems.

### Tekton CLI - tkn

tkn is a powerful cli to interact with Tekton inside of a k8s environment. Install the [tkn cli](https://github.com/tektoncd/cli) and add it to your path.

Installing Tekton in our k8s cluster of choice.

```bash
kubectl apply -f ./tekton-install/tekton-install.yaml
```

You can get the latest version of Tekton yamls from [here](https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml). I have saved them into the [tekton-install.yaml](./tekton-install/tekton-install.yaml) and it's a good practice to have them in source control for later inspection and updating cycles.
