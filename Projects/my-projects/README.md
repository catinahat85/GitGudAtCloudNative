# 🌐 BeatsintheCloud 🚀
---

## 📜 Project Overview

This project is structured in phases, with each phase building on the previous one to expand functionality, improve performance, and solve real-world challenges in cloud and DevOps. From initial managed deployments to fully self-hosted infrastructure, this project demonstrates a comprehensive approach to modern infrastructure management.

### Phases Included:
1. **Phase 1: Managed K8s Deployment with GitOps** - Initial deployment using DigitalOcean’s managed Kubernetes and GitOps automation.
2. **Phase 2: Self-Managed K3s Setup** - Migration to a self-hosted K3s environment on Hetzner for cost savings and greater control.
3. **Phase 3: Streamlined Architecture** - Integrating Ghost directly into K3s and removing multi-cloud dependencies.
4. **Phase 4: Security Hardening** - Enhancing security with intrusion detection, Cloudflare DDOS protection, and two-factor authentication.
5. **Phase 5: Service Mesh with Linkerd** - Implementing Linkerd for internal traffic management within the K3s cluster.
6. **Phase 6: Global Optimization with CDN** - Using AWS CloudFront as a CDN to improve asset delivery for a global audience.
7. **Phase 7: Future Enhancements** - Plans for additional cost optimizations, vertical scaling, failover setups, and feature expansions.

---

## ⚙️ Technologies and Tools Used

Throughout each phase, I utilized a range of tools and technologies, including:

- **Kubernetes & K3s** - Initial managed Kubernetes setup, later transitioning to self-hosted K3s.
- **GitOps with ArgoCD** - GitOps-driven automation for seamless deployments across phases.
- **Docker** - Containerized services for efficient deployment and management.
- **Monitoring & Observability** - Prometheus, Grafana, and later Linkerd for enhanced network observability.
- **Security Tools** - Falco for intrusion detection, Cloudflare for DDOS protection, and enhanced access controls.
- **Service Mesh** - Linkerd for managing internal service communication and securing traffic within the cluster.
- **Content Delivery Network** - AWS CloudFront to reduce latency and improve global asset delivery.

---

## 🔍 Phase-by-Phase Breakdown

### Phase 1: Managed K8s Deployment with GitOps
- **Objective**: Establish the project infrastructure on DigitalOcean’s managed Kubernetes with GitOps for automated deployments.
- **Details**: Initial setup deployed a static landing page and a Ghost blog on a managed Kubernetes cluster. GitOps practices with ArgoCD ensured smooth deployment from source to production.
- **Outcome**: Automated deployment pipeline was established, providing a solid foundation for further development.

### Phase 2: Self-Managed K3s Setup on Hetzner
- **Objective**: Reduce costs and gain more control by migrating to a self-hosted K3s cluster on Hetzner.
- **Details**: Moved all services to a Hetzner VPS running K3s. Prometheus, Grafana, and K9s replaced DigitalOcean’s native tools, while GitOps and ArgoCD managed deployments. Consolidated to a single cloud provider to minimize complexity.
- **Outcome**: Significant cost savings, reduced network complexity, and minimal downtime during the migration.

### Phase 3: Streamlined Architecture
- **Objective**: Simplify architecture by removing multi-cloud dependencies and reducing latency.
- **Details**: Integrated Ghost directly within the K3s cluster, deploying it in an isolated namespace and disabling ArgoCD reconciliation to prevent redeployment issues.
- **Outcome**: Improved performance, lower latency, and streamlined management with a fully self-hosted setup.

### Phase 4: Security Hardening
- **Objective**: Strengthen security with proactive monitoring and access control.
- **Details**: Added Falco for intrusion detection with real-time alerts, two-factor authentication for Ghost admin, and Cloudflare for DNS and DDOS protection.
- **Outcome**: Increased security readiness with best practices in place for production environments.

### Phase 5: Service Mesh with Linkerd
- **Objective**: Optimize internal service communication with a lightweight service mesh.
- **Details**: Implemented Linkerd for encrypted, efficient inter-service communication and observability, improving network security and load balancing.
- **Outcome**: Enhanced traffic control and monitoring, with improved performance and internal traffic management.

### Phase 6: Global Optimization with CDN
- **Objective**: Enhance performance for a global user base by offloading static content.
- **Details**: Integrated AWS CloudFront to cache and serve static assets, reducing workload on the K3s cluster and optimizing delivery speeds.
- **Outcome**: Faster load times for international users and improved user experience.

### Phase 7: Future Enhancements
- **Next Steps**:
   - **Failover and Multi-Cloud Setup** - Explore active/passive failover for improved reliability.
   - **Advanced CI/CD Enhancements** - Multi-branch support and enhanced testing capabilities.
   - **Extended Observability** - Addition of ELK for detailed logging insights.
   - **Vertical and Horizontal Scaling** - For high availability and to support website expansion
   - **New Hosting Options** - Potential migration to a cost-effective provider with robust features.

---

## 🌌 What I Learned

This project represents my journey in DevOps and Cloud Computing, 4 years in the making, with valuable lessons in:
- **Infrastructure Design** - Importance of consolidating resources for performance and cost management.
- **Automation** - Streamlining deployments with GitOps and CI/CD for consistency.
- **Security Best Practices** - Implementing proactive security measures for cloud-native environments.
- **Cost Efficiency** - Leveraging affordable cloud providers and tools to stay within budget.
- **Troubleshooting and Adaptation** - Overcoming real-world challenges in multi-cloud, networking, and security.

---

