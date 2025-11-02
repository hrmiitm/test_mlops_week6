# Kubernetes Pod vs Docker Container - Explanation

## Docker Container
- **Lightweight runtime** that packages application code, dependencies, and runtime
- **Single process** - runs one application per container
- **Isolation** at OS level using cgroups and namespaces
- **Example**: Your iris-api container with FastAPI server
- **Lifecycle**: Start/stop manually or via container orchestration
- **Resource overhead**: Minimal

## Kubernetes Pod
- **Wrapper around one or more containers** (usually one container per pod)
- **Smallest deployable unit** in Kubernetes
- **Shared network namespace** - containers in a pod share IP address
- **Ephemeral** - created and destroyed by controllers (Deployment, StatefulSet)
- **Lifecycle management** - auto-restart, auto-scaling, self-healing
- **Resource management** - CPU/memory requests and limits

## Key Differences

| Aspect | Docker Container | Kubernetes Pod |
|--------|------------------|-----------------|
| **Scope** | Single application instance | One or more containers |
| **Management** | Manual or external orchestration | Kubernetes automatically manages |
| **Networking** | Isolated network, port mapping | Shared IP within pod |
| **Persistence** | Manual volume management | StorageClass integration |
| **Scaling** | Manual container restart | Automatic replica scaling |
| **Resource Limits** | Not enforced by default | Enforced by Kubernetes |

## In Your Project
- **Docker**: iris-api container built from Dockerfile
- **Kubernetes Pod**: Wrapper around your iris-api container managed by the demo-iris-workload Deployment
- **Deployment Controller**: Creates 3 replicas (3 pods), each running iris-api container
