# Learn_DevOps

DevOps class assignments — **Utkarsh Pathak**, Enrollment No **24bcs10309**.

All ten homework assignments, each with a `README.md` containing the commands I ran, the **real output** captured from those runs, and an explanation of what the output means.

## Class Assignments

| # | Assignment | Submission link |
|---|---|---|
| 1 | Linux Fundamentals | [`Class_Assignments/Linux_Fundamentals/README.md`](Class_Assignments/Linux_Fundamentals/README.md) |
| 2 | Shell Scripting | [`Class_Assignments/Shell_Scripting/README.md`](Class_Assignments/Shell_Scripting/README.md) |
| 3 | Networking Fundamentals | [`Class_Assignments/Networking_Fundamentals/README.md`](Class_Assignments/Networking_Fundamentals/README.md) |
| 4 | Git & GitHub | [`Class_Assignments/Git-GitHub/README.md`](Class_Assignments/Git-GitHub/README.md) |
| 5 | Docker Fundamentals | [`Class_Assignments/Docker_Fundamental/README.md`](Class_Assignments/Docker_Fundamental/README.md) |
| 6 | DockerFiles & Images | [`Class_Assignments/DockerFiles_&_Images/README.md`](Class_Assignments/DockerFiles_&_Images/README.md) |
| 7 | Docker Networking & Volumes | [`Class_Assignments/Docker_Network/README.md`](Class_Assignments/Docker_Network/README.md) |
| 8 | Kubernetes Core Objects (Session 10) | [`Class_Assignments/Kubernetes/Session-10-K8s-Core-Objects/README.md`](Class_Assignments/Kubernetes/Session-10-K8s-Core-Objects/README.md) |
| 9 | Kubernetes Services (Session 11) | [`Class_Assignments/Kubernetes/Session-11-Kubernetes-Services/README.md`](Class_Assignments/Kubernetes/Session-11-Kubernetes-Services/README.md) |
| 10 | Ingress, ConfigMaps & Secrets (Session 12) | [`Class_Assignments/Kubernetes/Session-12-Ingress-ConfigMaps-Secrets/README.md`](Class_Assignments/Kubernetes/Session-12-Ingress-ConfigMaps-Secrets/README.md) |

All three Kubernetes sessions are indexed together in [`Class_Assignments/Kubernetes/README.md`](Class_Assignments/Kubernetes/README.md).

## What each assignment covers

**1. Linux Fundamentals** — soft vs hard links (proved with inode numbers and link counts), `adduser` vs `useradd`, and `journalctl`. Run inside an Ubuntu 24.04 container with **systemd actually running as PID 1**, so the journal output is genuine. Plus a worked Linux command cheat sheet.

**2. Shell Scripting** — a system information script using variables, `date`, `hostname`, `whoami`, `df`, `ps`, `read -p`, `mkdir`, `touch` and `>` / `>>` redirection, with the full run and the report file it produces.

**3. Networking Fundamentals** — 13 networking commands, each with real output and an explanation: `hostname`, `whoami`, `ip a`, `hostname -I`, `ip route`, `ping`, `nslookup`, `curl`, `ss`, `/etc/hosts`, `tracepath`, `traceroute`, `telnet`.

**4. Git & GitHub** — `git commit -m` vs `git commit -a -m` demonstrated on a tracked-modified file *and* an untracked file at the same time, then a cherry-pick of one specific commit out of three, with the commit graph showing the duplicated hash.

**5. Docker Fundamentals** — six Hello World web apps (Node.js, Python, Java, Apache, React, Nginx), each with its own folder and Dockerfile, all built, run, and verified in a browser.

**6. DockerFiles & Images** — a multi-stage Dockerfile serving *Hello World from Docker multi-stage build* on **port 8080**, measured against an identical single-stage build (**1.6GB → 194MB**), plus three multi-stage deployments each showing a different flavour of the technique.

**7. Docker Networking & Volumes** — three containers across three networks with the backend multi-homed and cross-tier isolation proved, Apache on the host network, a bind mount updating live with no restart, and a **real overlay network** built in swarm mode.

**8. Kubernetes Core Objects** — the five workload objects (Pod, ReplicaSet, Deployment, DaemonSet, StatefulSet), the full Pod lifecycle including `Pending`, `CrashLoopBackOff` and `ImagePullBackOff` triggered on purpose and diagnosed, and all four rollout strategies — **rolling update, blue-green, canary and recreate** — with the traffic measured during each switch, including the deliberate outage `Recreate` causes.

**9. Kubernetes Services** — all five Service types (ClusterIP, NodePort, LoadBalancer, ExternalName, headless), what each creates in the cluster, CoreDNS resolving service FQDNs, per-pod DNS records for a StatefulSet, and an endpoint-triage drill on a Service whose selector does not match its pods.

**10. Ingress, ConfigMaps & Secrets** — configuration kept out of the image with ConfigMaps and Secrets, the **base64 trailing-newline trap** that silently breaks Secret passwords shown byte by byte with `xxd`, and one NGINX Ingress doing host and path-based routing to a frontend and a backend that read from both objects.

## Evidence

Everything in these READMEs came from running the flow end to end on my own machine:

- **Output** is shown as captured text and as terminal screenshots, including the commands that failed and why.
- **Browser screenshots** are real captures of the pages served by my own running containers.
- **Terminal screenshots** are rendered from the captured output of those same commands.
- **Raw transcripts** and the scripts that produced them are committed under `*/lab/`, so any of it can be re-run.

Where something behaved differently than the task expected — a deprecated base image, a port already in use, a Docker Desktop platform limitation, a truncated HTTP response — it is documented with the actual error and the fix, rather than smoothed over.

## Environment

| | |
|---|---|
| Host | macOS (Apple Silicon, `arm64`) |
| Docker | `29.5.3`, Docker Desktop |
| Git | `2.51.0` |
| Linux environment | Ubuntu 24.04.4 LTS in Docker, with systemd as PID 1 |

Linux-only commands (`adduser`, `useradd`, `journalctl`, `ip`, `ss`, `tracepath`, `traceroute`) were run in the Ubuntu container, because macOS does not provide them. The Dockerfile for that environment is committed at [`Class_Assignments/Linux_Fundamentals/lab/Dockerfile`](Class_Assignments/Linux_Fundamentals/lab/Dockerfile).

## Course repository

Class material: [github.com/aryen1101/devops-heros](https://github.com/aryen1101/devops-heros)
