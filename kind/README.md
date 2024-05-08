# Create the K8s cluster

## How to deploy
- Check deployment prerequisites
```bash
❯ cd kind

❯ source .envrc

❯ docker version
Client: Docker Engine - Community
 Version:           26.1.1
 API version:       1.45
 Go version:        go1.21.9
 Git commit:        4cf5afa
 Built:             Tue Apr 30 11:47:53 2024
 OS/Arch:           linux/amd64
 Context:           default

Server: Docker Engine - Community
 Engine:
  Version:          26.1.1
  API version:      1.45 (minimum version 1.24)
  Go version:       go1.21.9
  Git commit:       ac2de55
  Built:            Tue Apr 30 11:47:53 2024
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.31
  GitCommit:        e377cd56a71523140ca6ae87e30244719194a521
 runc:
  Version:          1.1.12
  GitCommit:        v1.1.12-0-g51d5e94
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

❯ kind version
kind v0.22.0 go1.20.13 linux/amd64

❯ kubectl version
Client Version: v1.30.0
Kustomize Version: v5.0.4-0.20230601165947-6ce0bf390ce3
The connection to the server localhost:8080 was refused - did you specify the right host or port?
```

- Create the K8s cluster
```bash
❯ kind create cluster --config config.yaml
Creating cluster "github-arc-poc" ...
 ✓ Ensuring node image (kindest/node:v1.29.2) 🖼
 ✓ Preparing nodes 📦 📦 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
 ✓ Joining worker nodes 🚜
Set kubectl context to "kind-github-arc-poc"
You can now use your cluster with:

kubectl cluster-info --context kind-github-arc-poc

Not sure what to do next? 😅  Check out https://kind.sigs.k8s.io/docs/user/quick-start/
```

- Check the K8s cluster is created
```bash
❯ kind get clusters
github-arc-poc

❯ kubectl get nodes
NAME                           STATUS   ROLES           AGE   VERSION
github-arc-poc-control-plane   Ready    control-plane   71s   v1.29.2
github-arc-poc-worker          Ready    <none>          48s   v1.29.2
github-arc-poc-worker2         Ready    <none>          47s   v1.29.2
```

## How to undeploy
- Delete the K8s cluster
```bash
❯ kind delete cluster --name github-arc-poc
Deleting cluster "github-arc-poc" ...
Deleted nodes: ["github-arc-poc-control-plane" "github-arc-poc-worker" "github-arc-poc-worker2"]

❯ kind get clusters
No kind clusters found.
```
