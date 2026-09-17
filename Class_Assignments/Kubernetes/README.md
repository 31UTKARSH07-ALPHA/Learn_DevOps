# Kubernetes

**Name:** Utkarsh Pathak
**Enrollment No:** 24bcs10309

Sessions 10, 11 and 12 of the DevOps class, all run end to end on a local Minikube cluster and
written up one README per session.

| Session | Topic | Submission link |
|---|---|---|
| 10 | Kubernetes Core Objects, Pod Lifecycle & Deployment Strategies | [`Session-10-K8s-Core-Objects/README.md`](Session-10-K8s-Core-Objects/README.md) |
| 11 | Kubernetes Services & Cluster DNS | [`Session-11-Kubernetes-Services/README.md`](Session-11-Kubernetes-Services/README.md) |
| 12 | Ingress, ConfigMaps & Secrets | [`Session-12-Ingress-ConfigMaps-Secrets/README.md`](Session-12-Ingress-ConfigMaps-Secrets/README.md) |

## What each session covers

**Session 10 — Core objects and rollout strategies.** The five workload objects (Pod,
ReplicaSet, Deployment, DaemonSet, StatefulSet) and what each one adds over the last, the full
Pod lifecycle including the failure states (`Pending`, `CrashLoopBackOff`, `ImagePullBackOff`)
and the three probe types, then all four rollout strategies — rolling update, blue-green,
canary and recreate — each run to completion with the traffic measured during the switch.

**Session 11 — Services and DNS.** All five Service types (ClusterIP, NodePort, LoadBalancer,
ExternalName, headless), what each one actually creates in the cluster, how CoreDNS resolves a
service FQDN, and an endpoint-triage drill on a Service whose selector does not match its pods.

**Session 12 — Configuration and external access.** ConfigMaps and Secrets as the two ways to
keep configuration out of the image, the base64 trailing-newline trap that silently breaks
Secret-based passwords, and a single NGINX Ingress doing host and path-based routing to a
frontend and a backend that read their config from both objects.

## Environment

| | |
|---|---|
| Host | macOS 15 (Apple Silicon, `arm64`) |
| Kubernetes | Minikube `v1.39.0`, cluster `v1.37.0`, `docker` driver |
| kubectl | `v1.37.0` |
| Ingress | `ingress-nginx` controller `v1.15.1` via `minikube addons enable ingress` |

## Evidence

Every command block in these three READMEs was run against that cluster and its real output is
shown underneath it, including the commands that failed and why. The terminal screenshots are
rendered from those same captured runs, and the full raw transcripts are committed under each
session's `lab/` folder so any of it can be checked or re-run.

Three things in the class material do not work as written on macOS with the Docker driver, and
each is handled and explained where it comes up rather than skipped:

- `curl http://$(minikube ip):<nodePort>` — the node IP is not routable from the macOS host, so
  the in-cluster tests run from a curl Pod and the host-side tests use `minikube service --url`.
- A `LoadBalancer` Service stays `<pending>` forever on a local cluster, which is the correct
  result and is documented as such.
- `yatri.local` is reached by port-forwarding the ingress controller and sending a `Host:`
  header, instead of editing `/etc/hosts`.

## Course material

Class repository: [github.com/Nency-Ravaliya/devops-heros](https://github.com/Nency-Ravaliya/devops-heros)
— sessions `session10-k8s-core-objects`, `session-11-kubernetes-services` and
`session-12-ingress-configmaps-secrets`.
