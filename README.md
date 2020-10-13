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
kubectl apply -f ./tekton-yamls/02-param.yaml
```

starting the task :

```bash
tkn task start --showlog hello
```

We can also specify the parameters directly from the command line by using the -p argument.

```bash
tkn task start --showlog -p person=Shiva hello
```

### Multiple steps in a Task -3

Tekton tasks can have more than one step.

Applying the task to k8s environment

```bash
kubectl apply -f ./tekton-yamls/03-multistep.yaml
```

starting the task :

```bash
tkn task start --showlog hello
```

### Pipelines - 4

A Pipeline is a collection of Tasks that we define and arrange in a specific order of execution as part of our continuous integration flow.

Each Task in a Pipeline executes as a Pod on your Kubernetes cluster.

Applying the task and pipeline to the k8s environment :

```bash
kubectl apply -f ./demo/04-tasks.yaml
kubectl apply -f ./demo/05-pipeline.yaml
```

Executing the Pipeline :

```bash
tkn pipeline start say-things --showlog
```
