# Optimizing My Kubernetes Deployment

This further chronicles my setup and evolving workflow. It includes details on multi-cloud architecture, Kubernetes management, GitOps workflows, and more, with a focus on cost-efficiency, security, and scalability.

---

## Table of Contents
- [Initial Setup](#initial-setup)
- [Multi-Cloud Challenges](#multi-cloud-challenges)
- [Migration to K3s on Hetzner](#migration-to-k3s-on-hetzner)
- [Streamlining Architecture](#streamlining-architecture)
- [Security Hardening](#security-hardening)
- [Adding Linkerd Service Mesh](#adding-linkerd-service-mesh)
- [Global Performance with CloudFront CDN](#global-performance-with-cloudfront-cdn)
- [Future Steps](#future-steps)

---

## Initial Setup

I started with a simple landing page, intended as a focal point for my projects and learning materials, but I quickly wanted more control over the platform. Initially, I deployed:
- **WordPress on a Managed Service** - Quickly replaced by **Ghost on AWS** for a more lightweight experience.
- **Dockerized Ghost on AWS VM** - Ghost served through Nginx reverse proxy.  
- **Multi-Cloud Kubernetes** - Managed DigitalOcean Kubernetes, with AWS for specific workloads.  

Tools Used:
- **Prometheus** and **Grafana** for monitoring.
- **K9s** for terminal-based Kubernetes management.
- **GitHub & ArgoCD** for GitOps-driven deployments.
- **Cloudflare** for DNS and SSL/TLS.


---

## Multi-Cloud Challenges

![Initial Setup](https://beatsinthe.cloud/blog/content/images/2024/10/7CAFD523-BF78-4384-8CDB-DD9F92BEA7A1.jpeg)

### Pain Points:
1. **Traffic Management and Networking** - Managing connections across AWS and DigitalOcean led to network complexities.
2. **Cost Management** - Credits were running out, and maintaining two cloud providers was going to be costly.
3. **Configuration Consistency** - Maintaining consistent setups across clouds added operational overhead.

### Solution:
**Single Cloud Migration** - By moving everything to **Hetzner** under a self-hosted **K3s** setup, I simplified and streamlined management.

---

## Migration to K3s on Hetzner

1. **Setup K3s on Hetzner** - Installed K3s on Hetzner’s affordable VPS for better cost management.
2. **Reimplemented Monitoring** - Used **Prometheus**, **Grafana**, and **K9s** to replace DigitalOcean’s UI.
3. **GitOps Integration** - With GitOps and ArgoCD, migrating was seamless with near-zero downtime.

![Multi-Cloud Setup](https://beatsinthe.cloud/blog/content/images/2024/10/A0BEB0DE-D73E-4704-A989-75FF1835302C.jpeg)

### Benefits:
- **Cost Reduction** - Hetzner’s pricing saved significantly while providing robust resources.
- **Simplified Architecture** - Consolidated infrastructure reduced network latency and errors.

---

## Streamlining Architecture

The simplified setup eliminated the need for a multi-cloud reverse proxy setup, significantly reducing latency and management complexity. This paved the way for:
- **Direct Ghost Integration** - Hosting Ghost within the K3s cluster.
- **Namespace Isolation** - Ghost deployed in its own namespace with ArgoCD reconciliation disabled to avoid redeployment issues.

![Migration Setup](https://beatsinthe.cloud/blog/content/images/2024/10/E44CEACB-8E22-4BFE-ABEA-D57C9AE44A46.jpeg)

### Key Improvements:
- **Improved Performance** - Lower latency and faster load times.
- **Enhanced Observability** - All components monitored within the same environment.

---

## Security Hardening

With architecture in place, I focused on strengthening security:
1. **Firewalls & Intrusion Detection** - Deployed **Falco** for real-time Intrusion Detection and configured alerts via Slack.
2. **2FA for Ghost Admin** - Added two-factor authentication for secure access.
3. **Cloudflare Proxy** - Enabled DNS and DDOS protection via Cloudflare.

![Streamlined Architecture](https://beatsinthe.cloud/blog/content/images/2024/10/CDA12ECA-80E8-4A94-B668-3F8BA4287153.jpeg)

### Key Additions:
- **Falco IDS** - Real-time alerts for suspicious activity.
- **Enhanced Access Controls** - Security measures ensured production readiness.

---

## Adding Linkerd Service Mesh

To manage internal traffic, I introduced **Linkerd** for service-to-service communication within K3s:
1. **Traffic Management** - Improved control over network traffic and added load balancing.
2. **Network Observability** - Linkerd’s observability enhanced insights beyond Prometheus/Grafana.

![Security Setup](https://beatsinthe.cloud/blog/content/images/2024/10/EA370075-E0D9-4208-BB19-F580181988AF.jpeg)

### Why Linkerd?
- **Lightweight and Efficient** - Linkerd outperformed alternatives like Istio and Cilium in resource usage and simplicity.
- **Enhanced Security** - Encrypted inter-service communication and refined traffic policies.

---

## Global Performance with CloudFront CDN

To optimize global access:
1. **Integrated CloudFront CDN** - Cached static assets (images, JavaScript, CSS) for faster access worldwide.
2. **Reduced Cluster Load** - Offloading static content decreased workload on K3s.

![Linkerd Implementation](https://beatsinthe.cloud/blog/content/images/2024/10/EA370075-E0D9-4208-BB19-F580181988AF--1--1.jpeg)

### Result:
Improved user experience and reduced latency for users worldwide.

---

## Future Steps

- **Consolidate Further** - Exploring cheaper hosting options with comparable power for more savings.
- **Remote Container Registry** - Transitioning from DockerHub for a free multi-repo solution.
- **Scaling with New Services** - Planning for additional site elements (e.g., e-commerce and community forum) as the project grows.

---

This journey highlights the iterative process of refining cloud infrastructure, mastering cloud-native tools, and balancing performance with budget constraints. Stay tuned for future updates!
