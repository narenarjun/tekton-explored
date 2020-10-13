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

## Tasks

Tasks happen inside a pod. You can use tasks to perform various CI/CD operations.

### task - 1

applying the task to the k8s environment :

```bash
kubectl apply -f ./tekton-yamls/01-hello.yaml
```

Let's list all the tasks in our environment :

```bash
tkn task list
```

running the task :

```bash
tkn task start --showlog hello
```

### add parameter to task - 2

Tasks can also take parameters.

Applying the task to k8s environment :

```bash
kubectl apply -f ./demo/02-param.yaml
```

starting the task :

```bash
tkn task start --showlog hello
```

We can also specify the parameters directly from the command line by using the -p argument.

```bash
tkn task start --showlog -p person=Shiva hello
```
