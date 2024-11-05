# Deploying My Site on Kubernetes with GitHub Actions and Flux

So, I wanted a place to tie together everything. My music study crams, my deployments, the books, and this educational resource repo. So I made **[the repo](https://github.com/catinahat85/CloudFiLive)** for my main site, **[Beatsinthe.cloud](http://Beatsinthe.cloud)** public for you to observe or even fork. This repository contains the source code and configuration for my website, deployed on a Kubernetes cluster hosted on DigitalOcean. The deployment is automated using **GitHub Actions** and **Flux** to ensure that changes pushed to the repository are reflected in the live environment without manual intervention.

## Overview

I set up the **CI/CD pipeline** to automatically build and deploy changes to my site. The tools I used in this process are:

- **GitHub Actions**: Used to build the Docker image and push it to DockerHub when changes are committed to the repository.
- ~**Flux Image Reflector**: Watches for updated Docker images on DockerHub and automatically updates the Kubernetes deployment to reflect the changes.~
- **Argo CD Core**: I pivoted to Argo from Flux because it is easier to set up and use, has a cleaner UI, and provides intuitive, real-time monitoring of deployments compared to Flux. It’s more straightforward for lazy people like me who want faster results with less hassle.
- **Docker**: Containerizes the application for deployment in Kubernetes.
- **Kubernetes**: Orchestrates the deployment, scaling, and management of the containerized app.

## Project Structure

Here’s an overview of the important files and directories in this repo:

- `.github/workflows/Update docker-image.yml`: The GitHub Actions workflow that automates the Docker image build and push process.
- `./deployment.yaml`: Defines the Kubernetes deployment for the app.
- `service.yaml`: Configures the Kubernetes service to expose the app.
- `kustomization.yaml`: Manages customization of Kubernetes manifests.
- `Dockerfile`: Describes how the Docker image is built.

## Workflow Overview

### 1. GitHub Actions for CI

Whenever I commit changes to the repository, GitHub Actions triggers a workflow that:

- **Builds the Docker image** using the `Dockerfile`. Courtesy of Github Actions.
- **Pushes the updated image** to my DockerHub account.

This automates the image creation process, ensuring that the latest version of the site is always available.

### 2. ~Flux~ Argo CD for Continuous Deployment

~Flux~ Argo CD continuously monitors my DockerHub repository for changes to the app image. When a new image is detected, Flux:

- **Updates the Kubernetes deployment** with the new image.
- **Rolls out the changes** by replacing the old deployment with the new one, ensuring zero downtime during the update.

### 3. Kubernetes

Kubernetes handles the deployment and scaling of the containerized app. The app’s deployment and service are defined in the `deployment.yaml` and `service.yaml` files. These manifests define how the site runs and how it is exposed to the internet.

## How It Works

Here’s a high-level look at how the automation works:

1. Push updates to the repository (e.g., modifying `index.html` or `Dockerfile`).
2. GitHub Actions builds and pushes the new Docker image to DockerHub.
3. Argo detects the new image on DockerHub and updates the Kubernetes deployment.
4. Kubernetes rolls out the updated deploymet without any downtime.

## Tools Used

- **GitHub Actions**: For automating the CI process (Docker image build and push).
- **Argo**: For automating the CD process (monitoring and updating Kubernetes deployments).
- **Docker**: For containerizing the nginx app.

- **Kubernetes**: For orchestrating the containerized application in a cloud environment.
- **DigitalOcean**: As the cloud provider for hosting the Kubernetes cluster.
  
## Why This Setup?

This setup provides a fully automated CI/CD pipeline for deploying my site. Using GitHub Actions for CI and Argo for CD ensures that I can focus on the fun stuff (coding HTML, yay), while the deployment process is handled seamlessly. Also becauseI don't want alot of maintenance and wanted to show off. Also because I'm both lazy and a show off.

---

Now that you know what and how I did it, some musings and some key points to know:

# Key things to Know About DockerHub
If you're planniong on using for Production, maybe consider it twice.

Free tier users are subject to pull rate limits:
- **Anonymous users**: Up to **100 pulls per 6 hours**.
- **Authenticated users**: Up to **200 pulls per 6 hours**.
This can affect production environments relying on DockerHub for frequent image pulls, especially in larger deployments.

DockerHub automatically deletes **inactive images** that haven’t been pulled or updated in **6 months** if you're on the free tier. You must stay active to avoid losing images, which can be problematic if you're using old images for future deployments.

Public images can be accessed by anyone, which might expose your environment to potential vulnerabilities if not properly maintained. 
- Some public images may contain **security risks**, **outdated dependencies**, or even **malware**.
- I recommend always scanning public images before use and consider using Docker's image scanning feature for vulnerability detection. Has anyone given you the container image birds and the bees talk?

DockerHub API usage is also rate-limited, which can disrupt automated workflows in CI/CD pipelines. 
- Cache images locally or use a DockerHub mirror to reduce API requests and prevent hitting rate limits.

Free accounts are limited to **1 private repository**. If your project requires more, you’ll need to upgrade to a paid plan.
- Alternatives include image registries like **GitHub Packages** or **self-hosted registries** for private image hosting.

DockerHub is a centralized service, meaning **downtime** or **service interruptions** can affect your deployments. 
- Try mirroring images locally or set up a private registry for mission-critical applications to avoid downtime caused by DockerHub outages.
  - For example, I’ve implemented **Harbor** on my Kubernetes cluster for this purpose.


# Why My Setup IS IN FACT Overkill
Here are a few reasons why the setup I implemented could be considered over-engineered for this project:

## Single Node Deployment
- Running a **Kubernetes cluster** for a single-node website might be overkill. A simpler solution, such as using Docker directly on a virtual machine (VM), could achieve the same result with less complexity.
- Kubernetes is best suited for complex, multi-node environments, which isn't necessary for a basic or small-scale site.

## Automated CI/CD for Small Projects
- While using **GitHub Actions** and **Argo** for CI/CD is powerful, manually deploying the app or using a simpler CI tool could have been more efficient for a personal or small project.
- The level of automation might not be fully needed if updates and deployments happen infrequently.

## Argo for Image Reconciliation
- **Argo** automatically monitors DockerHub and updates the Kubernetes deployment with new images, but for a small site that rarely changes, manually updating the deployment would have been simpler and less resource-intensive.

## Horizontal Auto-scaling
- Enabling **auto-scaling** in Kubernetes is useful for high-traffic applications, but for a single-node personal website, it adds complexity without much benefit. Static resources or manually scaled environments could be easier to manage.

## Private Registry Setup (Harbor)
- Setting up a **self-hosted private Docker registry** like **Harbor** is typically done for enterprise-level security and control. For a personal project, using **DockerHub** or another public registry would likely be simpler and require less maintenance.

## High Availability Features
- Kubernetes provides features like **rolling updates** and **zero-downtime deployments**, which are overkill for a personal or small project. If the site doesn’t need high availability or frequent updates, a simpler deployment strategy could suffice.


# If you're looking to not spend much on Kubernetes
If you're looking for cost-effective (See: CHEAP) ways to run Kubernetes, consider these options, or if setting up a home lab is out of the question:

1. **DigitalOcean/Linode/Vultr/Civo**  
   They have low-cost managed Kubernetes services available on VPS providers. I get zero revenue from them. They're just cheap. There. I said it. But they charge for load balancers. And you kind of need those.

2. **K3s, Minikube or MicroK8s**  
   A lightweight Kubernetes distribution suitable for cloud VMs or edge devices. Could run on most free tier VMs offered by Oracle Cloud (I highly recommend trying them out), GCP, Azure or AWS. I like Canonical's work, don't let the snap-haters tell you otherwise, but I have a feeling you'll end up liking Minikube. Sorry K3s, you're the "Community" of light K8s distros, loved by your base, but continually failing to catch on with audiences. 6 Distros and a movie!

3. **Self-Hosted on Cloud VMs**  
   This is how I learned, got permanently suspended from OCI (It's ok, I appealed it and won many months later). Use cloud VMs from AWS, GCP, Azure, OVH, Civo, and Digital Ocean (by my experience OCI does not play well with self-hosted) to self-manage Kubernetes for lower costs. If you want to keep costs low, use the minimal K8s distros (Microk8s, Minoikube, k3s) and not vanilla.

4. **Bare Metal Kubernetes**  
   Rent bare metal servers for affordable, large-scale Kubernetes hosting. Rackspace spot instance often go for $17 A YEAR! - with a big caveat....It will likely get deleted out of nowhere. That's the caveat. Yikes.com

5. **Docker Desktop or OpenShift OKD**  
   Docker Desktop has a Kubernetes feature that has Kubectl installed for you to be able to run a small cluster locally. I've never tried Openshift. But I hear they're just lovely.


But if you want to do a project to show off....doing it on the cloud is the way to go.

---

As I said before, the point of this was to prove my abilities, prove that I know what I am talking about and show my work, per se.

- In 2020, I was making sites on Blogger and wordpress still. 
- In 2021 I was using AWS S3 to make an object public and use the external IP as the site.
- In 2022 I was finally using nginx and apache to manage my own servers on a VM with multiple sites.
- In 2023 I was reducing the resource usage by deploying those servers with Docker
- In 2024 I am fully multicloud, and now overdoing it by using Kubernetes, with high availability and automated CI/CD. All of this for under $24 a month. 

- And yeah, the blog section is on managed Wordpress. Sue me. I don't want to manage a WordPress site bro. I'd rather learn OpenStack. I'm not a web developer.

**Next up, I'll be working on monitoring and observability.**
