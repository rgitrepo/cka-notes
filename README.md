# CKA Exam Notes: Utilizing `kubectl run` and `kubectl create` Commands

## Handling YAML Files

Working with YAML files directly in the CLI can be cumbersome, especially under exam conditions where you need to copy and paste YAML content efficiently. The `kubectl run` and `kubectl create` commands can simplify this process by generating YAML templates or sometimes avoiding the need for manual YAML creation altogether.

### Simplifying YAML Creation with `kubectl`

#### Creating an NGINX Pod
To create a basic NGINX pod using `kubectl run`:
```bash
kubectl run nginx --image=nginx
```
This command creates a pod named `nginx` with the NGINX image.

#### Generating Pod Manifest YAML (without creating the pod)
To generate the YAML for an NGINX pod without actually creating it:
```bash
kubectl run nginx --image=nginx --dry-run=client -o yaml
```
- `--dry-run=client`: Validates the command without creating the resource.
- `-o yaml`: Outputs the resource definition in YAML format.

#### Creating a Deployment
To create a deployment with the NGINX image:
```bash
kubectl create deployment --image=nginx nginx
```
This command sets up a deployment named `nginx` with the NGINX image.

#### Generating Deployment YAML (without creating the deployment)
To generate the YAML for an NGINX deployment without creating it:
```bash
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml
```

#### Generating and Saving Deployment YAML
To generate the YAML for an NGINX deployment and save it to a file:
```bash
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml
```
- `> nginx-deployment.yaml`: Redirects the output to a file named `nginx-deployment.yaml`.

Make any necessary modifications to the `nginx-deployment.yaml` file (e.g., add more replicas) and then create the deployment using:
```bash
kubectl create -f nginx-deployment.yaml
```

#### Creating a Deployment with Specified Replicas (K8s version 1.19+)
To create a deployment with 4 replicas directly:
```bash
kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml
```
- `--replicas=4`: Specifies the number of replicas for the deployment.

### Reference
Bookmark the following page for the exam as it provides useful conventions and command usage: [Kubectl Conventions](https://kubernetes.io/docs/reference/kubectl/conventions/)

By utilizing these commands, you can efficiently generate and modify YAML templates, reducing the potential for errors and improving your workflow during the exam. Practice using these commands regularly to become adept at managing Kubernetes resources.
