# DevOps Zero

## Timeline at a glance

| Phase | Topic                         | Project                                  | Done |
| ----- | ----------------------------- | ---------------------------------------- | ---- |
| 1     | Linux, Networking, Git        | Linux web server + backup script         | ◻    |
| 2     | Scripting (Bash + Python)     | Server health monitor with alerts        | ◻    |
| 3     | Cloud (AWS)                   | Highly available 3-tier app on AWS       | ◻    |
| 4     | Docker                        | Containerized multi-service app          | ◻    |
| 5     | CI/CD                         | Full pipeline: build, test, push, deploy | ◻    |
| 6     | Infrastructure as Code        | Terraform modules + Ansible config       | ◻    |
| 7     | Kubernetes                    | App on Kubernetes with Helm              | ◻    |
| 8     | GitOps                        | ArgoCD continuous delivery               | ◻    |
| 9     | Monitoring and Logging        | Observability stack                      | ◻    |
| 10    | DevSecOps                     | Secured pipeline                         | ◻    |
| 11    | Capstone, portfolio, job prep | End-to-end capstone + interviews         | ◻    |

---

## Phase 1: Foundations — Linux, Networking, Git

**Learn:**

- Linux: file system, permissions, users and groups, processes, systemd, package managers, cron, SSH, `grep`, `sed`, `awk`, `curl`, `journalctl`
- Networking: IP addressing, subnets/CIDR, DNS, TCP vs UDP, HTTP/HTTPS, ports, firewalls, load balancers, NAT
- Git: clone, commit, branch, merge, rebase, pull requests, resolving conflicts, `.gitignore`, GitHub workflow

**Resources:**

- Linux Journey (linuxjourney.com), free and beginner friendly
- OverTheWire: Bandit wargame, practice Linux in a fun way
- *The Linux Command Line* by William Shotts (free PDF)
- Learn Git Branching (learngitbranching.js.org), interactive
- Pro Git book (git-scm.com/book), free
- Professor Messer's Network+ videos on YouTube for networking basics
- roadmap.sh/devops to keep the big picture in view

**Project 1: Linux Web Server from Scratch**

- Create an Ubuntu VM (VirtualBox or a free-tier cloud VM)
- Harden SSH (key-only login, disable root, change port optionally), set up UFW firewall
- Install and configure Nginx, serve a static site
- Write a script that backs up the site directory daily with cron
- Push everything with a clear README to GitHub

---

## Phase 2: Scripting — Bash and Python

**Learn:**

- Bash: variables, conditionals, loops, functions, exit codes, argument parsing, pipes and redirects
- Python: data types, functions, file I/O, JSON/YAML, `requests`, `subprocess`, `boto3` (AWS SDK), virtual environments
- Regex basics, working with APIs

**Resources:**

- freeCodeCamp: Python for Beginners and Bash scripting courses (YouTube)
- *Automate the Boring Stuff with Python* (free online)
- Bash scripting tutorial by Ryan's Tutorials or Shell Scripting for DevOps courses on YouTube
- Exercism.org (Bash and Python tracks) for daily practice

**Project 2: Server Health Monitor**

- Write a Python script that checks CPU, memory, disk usage and whether key services are running
- Send alerts via email or a Slack/Telegram webhook when thresholds are crossed
- Run it on a schedule with cron or a systemd timer
- Bonus: output a simple JSON report and keep history in a log file

---

## Phase 3: Cloud Fundamentals — AWS

**Learn:**

- IAM (users, roles, policies, least privilege), MFA, billing alarms
- EC2, AMIs, security groups, key pairs, EBS
- VPC: subnets, route tables, internet gateway, NAT gateway
- S3, RDS, Route 53, ELB (ALB), Auto Scaling Groups, CloudWatch
- AWS CLI

**Resources:**

- freeCodeCamp: AWS Certified Cloud Practitioner and Solutions Architect Associate courses (YouTube)
- Adrian Cantrill's AWS courses (paid, excellent depth) or Stephane Maarek on Udemy
- AWS Skill Builder (free tier of content) and AWS documentation
- Tutorials Dojo practice exams if you aim for the certification

**Project 3: Highly Available 3-Tier Web App on AWS (manual first)**

- Custom VPC with public and private subnets across 2 Availability Zones
- Web tier on EC2 behind an Application Load Balancer, in an Auto Scaling Group
- Database on RDS in private subnets
- Domain via Route 53 (optional) and HTTPS with ACM
- CloudWatch alarms and a billing alarm
- Draw the architecture diagram and put it in your README

**Certification checkpoint:** AWS Cloud Practitioner (optional) or Solutions Architect Associate (strongly recommended, can be done in parallel with later phases).

---

## Phase 4: Containers — Docker

**Learn:**

- Images, containers, layers, Dockerfile best practices, multi-stage builds
- Volumes, networks, environment variables
- Docker Compose for multi-container apps
- Registries: Docker Hub, Amazon ECR
- Image size optimization and running as non-root

**Resources:**

- TechWorld with Nana: Docker Tutorial for Beginners (YouTube)
- Docker official docs and "Get Started" guide
- KodeKloud Docker for the Absolute Beginner (hands-on labs)
- Play with Docker (labs.play-with-docker.com)

**Project 4: Containerize a Multi-Service App**

- Pick or build a simple app: frontend + backend API + database (e.g., Node/Flask + PostgreSQL + Redis)
- Write optimized Dockerfiles (multi-stage, small base images, non-root user)
- Orchestrate with Docker Compose including a volume for the DB and a healthcheck
- Push images to Docker Hub or ECR
- Deploy it on an EC2 instance using Compose

---

## Phase 5: CI/CD

**Learn:**

- CI/CD concepts, branching strategies (trunk-based, GitFlow)
- **GitHub Actions** (primary): workflows, jobs, runners, secrets, matrix builds, caching, reusable workflows
- **Jenkins** (secondary, widely asked in interviews): pipelines, Jenkinsfile, agents, plugins
- Automated testing, linting, artifact versioning, semantic versioning
- Deployment strategies: rolling, blue/green, canary

**Resources:**

- TechWorld with Nana: GitHub Actions and Jenkins tutorials (YouTube)
- GitHub Actions official documentation
- KodeKloud Jenkins course
- *The Phoenix Project* and *The DevOps Handbook* for culture and concepts

**Project 5: End-to-End CI/CD Pipeline**

- On every push: lint, run unit tests, build Docker image, scan it, push to registry
- On merge to main: automatically deploy to your EC2 or AWS environment
- Add a manual approval step for production
- Add status badges and Slack/email notifications
- Repeat the core pipeline in Jenkins to show you know both tools

---

## Phase 6: Infrastructure as Code — Terraform and Ansible

**Learn Terraform:**

- HCL syntax, providers, resources, variables, outputs, data sources
- State, remote state (S3 + DynamoDB locking), workspaces
- Modules, `for_each`, `count`, dynamic blocks
- Plan/apply workflow, drift, importing existing resources

**Learn Ansible:**

- Inventory, ad-hoc commands, playbooks, roles, variables, handlers, templates (Jinja2)
- Idempotency, Ansible Vault

**Resources:**

- freeCodeCamp: Terraform course (YouTube) and TechWorld with Nana Terraform tutorial
- HashiCorp Developer tutorials (developer.hashicorp.com/terraform/tutorials), free and official
- *Terraform: Up & Running* by Yevgeniy Brikman
- Jeff Geerling's *Ansible for DevOps* (book and YouTube series)

**Project 6: Rebuild Project 3 with Terraform + Ansible**

- Recreate the entire 3-tier AWS architecture as reusable Terraform modules (network, compute, database)
- Store state remotely in S3 with locking
- Use Ansible to configure servers (install Docker, deploy the app, harden the OS)
- Run `terraform plan` automatically on pull requests via GitHub Actions and `apply` on merge
- Support dev and prod environments with different variable files

**Certification checkpoint:** HashiCorp Terraform Associate.

---

## Phase 7: Kubernetes

**Learn:**

- Architecture: control plane, nodes, kubelet, etcd, API server
- Pods, ReplicaSets, Deployments, Services (ClusterIP, NodePort, LoadBalancer), Ingress
- ConfigMaps, Secrets, Namespaces, labels and selectors
- Volumes, PersistentVolumes, PersistentVolumeClaims, StatefulSets
- Probes, resource requests/limits, HPA autoscaling
- RBAC, NetworkPolicies, taints and tolerations
- **Helm** (package manager) and **Kustomize**
- Managed Kubernetes: Amazon EKS

**Resources:**

- TechWorld with Nana: Kubernetes Tutorial for Beginners (YouTube, full course)
- KodeKloud: Kubernetes for the Absolute Beginner and CKA course with labs
- Kubernetes official docs and tutorials (kubernetes.io/docs/tutorials)
- killer.sh and Killercoda for free browser-based practice
- *Kubernetes Up & Running* (book)
- Local practice with `kind` or `minikube`

**Project 7: Deploy Your App on Kubernetes**

- First locally on `kind`/`minikube`: Deployments, Services, Ingress, ConfigMaps, Secrets, PVC for the database
- Add liveness and readiness probes, resource limits, and an HPA
- Package it as a Helm chart with values for dev and prod
- Provision an EKS cluster with Terraform and deploy there
- Document how to tear it all down (EKS costs money; do not leave it running)

**Certification checkpoint:** CKA (Certified Kubernetes Administrator) or CKAD. Both are hands-on and highly respected.

---

## Phase 8: GitOps — ArgoCD

**Learn:**

- GitOps principles: Git as the single source of truth
- ArgoCD: Applications, sync policies, health checks, app-of-apps pattern
- Image update flow: CI builds image, updates manifest repo, ArgoCD syncs

**Resources:**

- TechWorld with Nana: ArgoCD tutorial (YouTube)
- ArgoCD official docs and getting-started guide

**Project 8: GitOps Delivery**

- Separate app repo and config repo
- CI pipeline builds and pushes the image, then commits the new tag to the config repo
- ArgoCD automatically deploys to the cluster, with rollback by reverting a commit
- Deploy to two environments (staging and production) from different branches or folders

---

## Phase 9: Monitoring, Logging and Observability 

**Learn:**

- Metrics, logs, traces and the "golden signals" (latency, traffic, errors, saturation)
- **Prometheus** (PromQL, exporters, alerting rules) and **Alertmanager**
- **Grafana** dashboards
- Centralized logging: Loki (or the ELK/EFK stack)
- SLIs, SLOs, incident response basics, writing postmortems

**Resources:**

- TechWorld with Nana: Prometheus and Grafana tutorials (YouTube)
- Prometheus and Grafana official docs and Grafana's free learning journeys
- *Site Reliability Engineering* book (free at sre.google/books)

**Project 9: Observability Stack**

- Install kube-prometheus-stack with Helm on your cluster
- Instrument your app with custom metrics (a `/metrics` endpoint)
- Build Grafana dashboards for the app and the cluster
- Add alert rules (high error rate, pod crash looping, high latency) routed to Slack
- Add Loki for logs and write a short "incident" postmortem after deliberately breaking something

---

## Phase 10: DevSecOps 

**Learn:**

- Shifting security left: SAST, dependency scanning, container image scanning, secret scanning
- Tools: Trivy, SonarQube, Gitleaks, OWASP Dependency-Check
- Secrets management: AWS Secrets Manager, HashiCorp Vault, Sealed Secrets or External Secrets
- Kubernetes security: RBAC, Pod Security Standards, network policies
- Basics of the OWASP Top 10

**Resources:**

- TryHackMe and Kubernetes security tutorials
- Trivy and SonarQube documentation
- Aqua Security and Snyk learning content (free)

**Project 10: Secure the Pipeline**

- Add Gitleaks, SonarQube/SAST, and Trivy scans to your CI pipeline, failing the build on critical findings
- Move all secrets out of Git into a secrets manager
- Add a Kubernetes NetworkPolicy and run containers as non-root with read-only filesystems
- Write a short security summary in your README

---

## Phase 11: Capstone, Portfolio and Job Prep

- A real microservices app (3+ services)
- Infrastructure fully in Terraform (VPC, EKS, ECR, RDS)
- GitHub Actions CI with tests, scans, and image builds
- ArgoCD GitOps deployments to staging and production
- Prometheus/Grafana/Loki observability with alerts
- Secrets management and security scanning
- A clear architecture diagram, runbook, and cost-estimate section in the README

**Portfolio checklist:**

- 6–8 polished repos with READMEs, diagrams, and screenshots
- Pinned repos on GitHub, a clean profile README
- A technical blog (Medium, Dev.to or Hashnode): write one post per phase explaining what you built and what went wrong. This also cements your learning.
- LinkedIn updated with keywords: AWS, Terraform, Kubernetes, Docker, CI/CD, GitHub Actions, ArgoCD, Prometheus

**Interview preparation:**

- Be able to explain, from memory: what happens when you type a URL in the browser, how a Docker container differs from a VM, how a pod gets scheduled, how a CI/CD pipeline you built works, and how you would debug a crashing pod
- Practice scenario questions: "Production is down, what do you do?", "How would you design zero-downtime deployments?"
- Do mock interviews with a friend or use resources such as the DevOps interview lists on GitHub (e.g., *devops-exercises* by bregman-arie)
- Practice live troubleshooting on KodeKloud and Killercoda challenges

**Job search:**

- Target titles: Junior DevOps Engineer, Cloud Engineer, Site Reliability Engineer (junior), Platform Engineer, Build/Release Engineer, Systems Administrator moving to DevOps
- Start applying around week 36–40, not after finishing everything. Interviews are also practice.
- Contribute to an open-source DevOps project (even documentation fixes) to show collaboration.

## Certifications worth considering (in priority order)

1. **AWS Solutions Architect Associate** (or Cloud Practitioner first if you are new to cloud)
2. **HashiCorp Terraform Associate**
3. **CKA** or **CKAD**
4. Optional later: AWS DevOps Engineer Professional

## Free and low-cost resources summary

- **YouTube channels:** TechWorld with Nana, freeCodeCamp, KodeKloud, DevOps Directive, Jeff Geerling, TechWorld, Cantrill (previews), ahmedeidsec, Kube-ops
- **Hands-on labs:** KodeKloud, Killercoda, Play with Docker, AWS Free Tier, TryHackMe, https://kube-ops.com/en/labs 
