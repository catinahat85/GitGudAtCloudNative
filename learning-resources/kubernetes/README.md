# Kubernetes Learning Resources
My philosophy is this: Container orchestration is here to stay. It is becoming ubiquitous at a rapid pace, and the rise of AI will only accelerate this. Getting to know "the cloud" is only the beginning, so even having a basic familiarity with Cloud Native technologies is a must if you're looking to kick-start your career as a "Cloud Engineer" (which is basically an umbrella term more than a role nowadays).

## So What Is "Cloud Native"?
In short, it is technology meant to take advantage of cloud computing environments, their scaling capabilities, compute power, and their decentralized nature. 

According to the **[CNCF or, Cloud Native Computing Foundation](https://www.cncf.io)**, the leading organization in steering the way for Cloud Native technologies, Cloud Native is defined as:
"Cloud native practices empower organizations to develop, build, and deploy workloads in computing environments (public, private, hybrid cloud) to meet their organizational needs at scale in a programmatic and repeatable manner. It is characterized by loosely coupled systems that interoperate in a secure, resilient, manageable, sustainable, and observable manner. Cloud Native technologies and architectures typically consist of some combination of containers, service meshes, multi-tenancy, microservices, immutable infrastructure, serverless, and declarative APIs"

So, think of the following:
- Container Orchestration (Kubernetes, Google Borg, Docker Borg, Docker Swarm, Openshift)
- Containers (Docker, etc)
- Data Lakes (Delta Lake)
- Service Meshes
- Microservices
- Serverless Computing
- API Gateways
- Observation and Monitoring Tools

Feel intimidated yet? Don't be. Baby steps. I was learning once, and still am, and this is intended to share my journey, past and ongoing. So you're not alone.


## Index
1. [Get Started with Docker](#get-started-with-docker)
2. [My Aggregated Study Notes, Perfect for KCNA](#my-aggregated-study-notes)
3. [Introductory Kubernetes Courses](#introductory-kubernetes-courses)
4. [K8s Video Theory](#k8s-video-theory)
5. [Kubernetes Hands-On Learning Resources](#kubernetes-hands-on-learning-resources)
6. [Installing Kubernetes Locally?](#installing-kubernetes-locally)


---

## Get Started with Docker
If you’re new to containerization, these resources will help you get started with Docker.

- **[Deploy Cloud-Native Apps Using Azure Container Apps](https://learn.microsoft.com/en-us/credentials/applied-skills/deploy-cloud-native-apps-using-azure-container-apps/)**: Microsoft Learn’s module that teaches how to deploy cloud-native applications using Azure Container Apps, ideal for Azure enthusiasts.

- **[Docker Essentials - Cognitive Class](https://cognitiveclass.ai/courses/docker-essentials)**: A beginner-level course on Docker, covering container basics, how to work with Docker images and containers, and managing Docker Hub.

---

## My Aggregated Study Notes
- **[Study Notes](https://github.com/catinahat85/gitgudatcloudnative/blob/70f4545885a26737713b22d0980f54445fcb4451/learning-resources/Kubernetes%20Cloud%20Native%20Study%20Guide.pdf)**: Taken from a variety of sources, including the official docs, they have been beneficial when I have been stuck. If you're considering going for your KCNA, these are great to read over.
- **[Lofi Study Cram](https://www.youtube.com/watch?v=ipDBBMcSJDM&ab_channel=CloudFiBeats)**: A relaxed, narrated version of the study notes created with AWS Polly, set over my own Lofi beats meant for you to listen to while exercising, driving or working. it works for me, so I figured I'd share.

---

## Introductory Kubernetes Courses
Not sure what Kubernetes (K8s) is? Start here with these foundational courses.

- **[Linux Foundation Introduction to Kubernetes](https://training.linuxfoundation.org/training/introduction-to-kubernetes/)**: Official introductory course by the Linux Foundation.
  
- **[Linux Foundation Introduction to Kubernetes on EdX](https://www.edx.org/learn/kubernetes/the-linux-foundation-introduction-to-kubernetes)**: The same official course, hosted on EdX.

- **[Civo Academy](https://www.civo.com/academy)**: Free Kubernetes and cloud-native technology courses covering the essentials of cloud-native development, containers, and Kubernetes.

---

## K8s Video Theory 
A couple of reccomended videos that explain Kubernetes concepts, uses cases etc.

- **[Learn Kubernetes - KodeKloud](https://youtu.be/XuSQU5Grv1g?si=cRYIMRJ74BC4FiT0)**: A comprehensive beginner-friendly introduction to Kubernetes by KodeKloud, covering the core concepts and practical demonstrations.

- **[Kubernetes Tutorial - Techworld with Nana](https://youtu.be/X48VuDVv0do?si=WtiwUqi1CHDnJum_)**: Another excellent Kubernetes tutorial by Techworld with Nana, offering clear explanations and hands-on examples.

---

## Kubernetes Hands-On Learning Resources
Here you will find resources to help you practice Kubernetes with real-world, hands-on labs and environments.

- **[Google Cloud Kubernetes Lab](https://www.cloudskillsboost.google/course_templates/783)**: Hands-on Kubernetes lab offered by Google Cloud.

- **[KillerCoda](https://killercoda.com/)**: An interactive learning platform for Kubernetes with real scenarios.

- **[Killer Shell](https://killer.sh/)**: Practice environment for Kubernetes, great for preparing for the CKA/CKAD exams.

- **[Play with K8s](https://labs.play-with-k8s.com/)**: A free tool that lets you create Kubernetes clusters in your browser and experiment.

- **[IBM Kubernetes Service Tutorials](https://www.ibm.com/products/kubernetes-service/kubernetes-tutorials)**: IBM’s collection of Kubernetes tutorials to help you get started with managing applications in Kubernetes clusters using the IBM Kubernetes Service.

- **[Get Started with Kubernetes](https://collabnix.github.io/kubelabs/)**: An amazing list of Kubernetes Labs and Tutorials
---

## Installing Kubernetes Locally
Ready to start working with K8s locally? Here are some ways to do it. Docker Desktop and Multipass are probably easiest, but if you are up for it, spin up Minikube or K3s!


- **[MicroK8s with Multipass](https://microk8s.io/docs/install-multipass)**: MicroK8s is a small, fast, and secure Kubernetes installation from Canonical, ideal for local setups. Multipass creates isolated VMs to run MicroK8s, simplifying the process of spinning up Kubernetes clusters on your local machine.

- **[Docker Desktop Kubernetes](https://docs.docker.com/desktop/kubernetes/)**: Docker Desktop includes a simple way to enable a single-node Kubernetes cluster on your local machine. If you are already using Docker for container development, this is an easy way to integrate Kubernetes into your workflow.

- **[Minikube](https://minikube.sigs.k8s.io/docs/)**: Minikube is a tool that lets you run Kubernetes locally on your machine. It supports all Kubernetes features and is an excellent option for beginners who want a full Kubernetes experience on their local machine.

- **[K3s](https://k3s.io/)**: Lightweight Kubernetes distribution by Rancher Labs. K3s is a simplified and minimal installation of Kubernetes that works well for local development and testing, particularly on edge devices or low-resource environments.



