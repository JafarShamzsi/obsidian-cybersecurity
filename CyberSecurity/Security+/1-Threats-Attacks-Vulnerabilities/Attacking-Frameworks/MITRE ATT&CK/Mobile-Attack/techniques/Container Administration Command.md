---
alias: T1609
---

## T1609

Adversaries may abuse a container administration service to execute commands within a container. A container administration service such as the Docker daemon, the Kubernetes API server, or the kubelet may allow remote management of containers within an environment.(Citation: Docker Daemon CLI)(Citation: Kubernetes API)(Citation: Kubernetes Kubelet)

In Docker, adversaries may specify an entrypoint during container deployment that executes a script or command, or they may use a command such as <code>docker exec</code> to execute a command within a running container.(Citation: Docker Entrypoint)(Citation: Docker Exec) In Kubernetes, if an adversary has sufficient permissions, they may gain remote execution in a container in the cluster via interaction with the Kubernetes API server, the kubelet, or by running a command such as <code>kubectl exec</code>.(Citation: Kubectl Exec Get Shell)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Execution]] (TA0002)

### Platforms
- Containers

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Limit Access to Resource Over Network\|M1035]] | Limit Access to Resource Over Network | Limit communications with the container service to managed and secured channels, such as local Unix sockets or remote access via SSH. Require secure port access to communicate with the APIs over TLS by disabling unauthenticated access to the Docker API and Kubernetes API Server.(Citation: Docker Daemon Socket Protect)(Citation: Kubernetes API Control Access) In Kubernetes clusters deployed in cloud environments, use native cloud platform features to restrict the IP ranges that are permitted to access to API server.(Citation: Kubernetes Cloud Native Security) Where possible, consider enabling just-in-time (JIT) access to the Kubernetes API to place additional restrictions on access.(Citation: Microsoft AKS Azure AD 2023) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Use read-only containers, read-only file systems, and minimal images when possible to prevent the execution of commands.(Citation: Kubernetes Hardening Guide) Where possible, also consider using application control and software restriction tools (such as those provided by SELinux) to restrict access to files, processes, and system calls in containers.(Citation: Kubernetes Security Context) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Enforce authentication and role-based access control on the container service to restrict users to the least privileges required.(Citation: Kubernetes Hardening Guide) When using Kubernetes, avoid giving users wildcard permissions or adding users to the `system:masters` group, and use `RoleBindings` rather than `ClusterRoleBindings` to limit user privileges to specific namespaces.(Citation: Kubernetes RBAC) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Ensure containers are not running as root by default. In Kubernetes environments, consider defining Pod Security Standards that prevent pods from running privileged containers and using the `NodeRestriction` admission controller to deny the kublet access to nodes and pods outside of the node it belongs to.(Citation: Kubernetes Hardening Guide) (Citation: Kubernetes Admission Controllers) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Remove unnecessary tools and software from containers. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1609
- Docker Exec: https://docs.docker.com/engine/reference/commandline/exec/
- Docker Entrypoint: https://docs.docker.com/engine/reference/run/#entrypoint-default-command-to-execute-at-runtime
- Docker Daemon CLI: https://docs.docker.com/engine/reference/commandline/dockerd/
- Kubectl Exec Get Shell: https://kubernetes.io/docs/tasks/debug-application-cluster/get-shell-running-container/
- Kubernetes Kubelet: https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet/
- Kubernetes API: https://kubernetes.io/docs/concepts/overview/kubernetes-api/
