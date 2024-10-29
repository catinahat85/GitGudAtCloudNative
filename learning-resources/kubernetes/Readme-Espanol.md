# Recursos de Aprendizaje de Kubernetes

Mi filosofía es esta: la orquestación de contenedores llegó para quedarse. Se está volviendo omnipresente a gran velocidad, y el auge de la IA solo acelerará esto. Conocer "la nube" es solo el comienzo, por lo que incluso tener un conocimiento básico de las tecnologías Cloud Native es imprescindible si deseas iniciar tu carrera como "Ingeniero en la Nube" (un término amplio más que un rol específico hoy en día).

## Entonces, ¿Qué es "Cloud Native"?
En resumen, es tecnología diseñada para aprovechar los entornos de computación en la nube, sus capacidades de escalabilidad, potencia de cómputo y su naturaleza descentralizada.

Según la **[CNCF o Fundación de Computación Cloud Native](https://www.cncf.io)**, la organización líder en dirigir el camino para las tecnologías Cloud Native, Cloud Native se define como:
"Las prácticas Cloud Native permiten a las organizaciones desarrollar, construir y desplegar cargas de trabajo en entornos de cómputo (nube pública, privada, híbrida) para satisfacer sus necesidades organizacionales a escala de manera programática y repetible. Se caracteriza por sistemas débilmente acoplados que interoperan de manera segura, resiliente, manejable, sostenible y observable. Las tecnologías y arquitecturas Cloud Native suelen consistir en una combinación de contenedores, mallas de servicios, multitenencia, microservicios, infraestructura inmutable, computación sin servidor y APIs declarativas."

Así que piensa en lo siguiente:
- Orquestación de Contenedores (Kubernetes, Google Borg, Tanzu, Docker Swarm, Openshift)
- Contenedores (Docker, Podman)
- Lagos de Datos (Delta/Data Lake)
- Mallas de Servicios (Service Mesh) - Istio, Cilium, Linkerd, Consul
- Microservicios
- Computación sin Servidor
- GitOps Reconciliadores - Flux, Argo
- Puertas de enlace de API
- Herramientas de Observación y Monitoreo (Grafana, Prometheus, K9s)

¿Te sientes intimidado? No te preocupes. Paso a paso. Yo también estuve aprendiendo y sigo en ello, y esto está pensado para compartir mi viaje, pasado y en curso. Así que no estás solo.

## Índice
1. [Comienza con Docker](#comienza-con-docker)
2. [Mis Notas de Estudio Agregadas, Perfectas para KCNA](#mis-notas-de-estudio-agregadas)
3. [Cursos Introductorios de Kubernetes](#cursos-introductorios-de-kubernetes)
4. [Teoría de Kubernetes en Video](#teoría-de-kubernetes-en-video)
5. [Recursos de Aprendizaje Práctico de Kubernetes](#recursos-de-aprendizaje-práctico-de-kubernetes)
6. [¿Instalar Kubernetes Localmente?](#instalar-kubernetes-localmente)

---

## Comienza con Docker
Si eres nuevo en la contenedorización, estos recursos te ayudarán a comenzar con Docker.

- **[Despliega Aplicaciones Cloud-Native Usando Azure Container Apps](https://learn.microsoft.com/en-us/credentials/applied-skills/deploy-cloud-native-apps-using-azure-container-apps/)**: Módulo de Microsoft Learn que enseña cómo desplegar aplicaciones Cloud Native usando Azure Container Apps, ideal para entusiastas de Azure.

- **[Docker Essentials - Cognitive Class](https://cognitiveclass.ai/courses/docker-essentials)**: Curso de nivel principiante sobre Docker, cubriendo los conceptos básicos de los contenedores, cómo trabajar con imágenes y contenedores de Docker, y gestionar Docker Hub.

---

## Mis Notas de Estudio Agregadas
- **[Notas de Estudio](https://github.com/catinahat85/GitGudAtCloudNative/blob/main/learning-resources/kubernetes/Gui%CC%81a%20de%20estudio%20sobre%20Kubernetes%20y%20Cloud%20Native.docx)**: Tomadas de una variedad de fuentes, incluidas las documentaciones oficiales, han sido útiles cuando me he quedado atascado. Si estás considerando obtener tu KCNA, son excelentes para leer.

- **[Lofi Study Cram](https://www.youtube.com/watch?v=ipDBBMcSJDM&ab_channel=CloudFiBeats)**: Una versión narrada y relajada de las notas de estudio creadas con AWS Polly, con mis propios beats Lofi para que escuches mientras haces ejercicio, manejas o trabajas. Funciona para mí, así que pensé en compartirlo.

---

## Cursos Introductorios de Kubernetes
¿No estás seguro de qué es Kubernetes (K8s)? Comienza aquí con estos cursos básicos.

- **[Introducción a Kubernetes de Linux Foundation](https://training.linuxfoundation.org/training/introduction-to-kubernetes/)**: Curso introductorio oficial de la Linux Foundation.
  
- **[Introducción a Kubernetes de Linux Foundation en EdX](https://www.edx.org/learn/kubernetes/the-linux-foundation-introduction-to-kubernetes)**: El mismo curso oficial, alojado en EdX.

- **[Civo Academy](https://www.civo.com/academy)**: Cursos gratuitos sobre Kubernetes y tecnologías Cloud Native, cubriendo los conceptos básicos del desarrollo Cloud Native, contenedores y Kubernetes.

---

## Teoría de Kubernetes en Video
Algunos videos recomendados que explican conceptos de Kubernetes, casos de uso, etc.

- **[Aprende Kubernetes - KodeKloud](https://youtu.be/XuSQU5Grv1g?si=cRYIMRJ74BC4FiT0)**: Una introducción completa y amigable para principiantes a Kubernetes por KodeKloud, cubriendo los conceptos básicos y demostraciones prácticas.

- **[Tutorial de Kubernetes - Techworld with Nana](https://youtu.be/X48VuDVv0do?si=WtiwUqi1CHDnJum_)**: Otro excelente tutorial de Kubernetes por Techworld with Nana, que ofrece explicaciones claras y ejemplos prácticos.

---

## Recursos de Aprendizaje Práctico de Kubernetes
Aquí encontrarás recursos para ayudarte a practicar Kubernetes con laboratorios prácticos y entornos reales.

- **[Laboratorio de Kubernetes en Google Cloud](https://www.cloudskillsboost.google/course_templates/783)**: Laboratorio práctico de Kubernetes ofrecido por Google Cloud.

- **[KillerCoda](https://killercoda.com/)**: Una plataforma de aprendizaje interactiva para Kubernetes con escenarios reales.

- **[Killer Shell](https://killer.sh/)**: Entorno de práctica para Kubernetes, ideal para prepararse para los exámenes CKA/CKAD.

- **[Play with K8s](https://labs.play-with-k8s.com/)**: Una herramienta gratuita que te permite crear clústeres de Kubernetes en tu navegador y experimentar.

- **[Tutoriales del Servicio de Kubernetes de IBM](https://www.ibm.com/products/kubernetes-service/kubernetes-tutorials)**: Colección de tutoriales de Kubernetes de IBM para ayudarte a empezar a gestionar aplicaciones en clústeres de Kubernetes usando el Servicio de Kubernetes de IBM.

- **[Comienza con Kubernetes](https://collabnix.github.io/kubelabs/)**: Una lista increíble de Laboratorios y Tutoriales de Kubernetes.

---

## Instalar Kubernetes Localmente
¿Listo para empezar a trabajar con K8s localmente? Aquí tienes algunas formas de hacerlo. Docker Desktop y Multipass son probablemente las opciones más fáciles, pero si te atreves, pon en marcha Minikube o K3s.

- **[MicroK8s con Multipass](https://microk8s.io/docs/install-multipass)**: MicroK8s es una instalación de Kubernetes pequeña, rápida y segura de Canonical, ideal para configuraciones locales. Multipass crea máquinas virtuales aisladas para ejecutar MicroK8s, simplificando el proceso de crear clústeres de Kubernetes en tu máquina local.

- **[Kubernetes en Docker Desktop](https://docs.docker.com/desktop/kubernetes/)**: Docker Desktop incluye una forma sencilla de habilitar un clúster de Kubernetes de un solo nodo en tu máquina local. Si ya usas Docker para el desarrollo de contenedores, esta es una forma fácil de integrar Kubernetes en tu flujo de trabajo.

- **[Minikube](https://minikube.sigs.k8s.io/docs/)**: Minikube es una herramienta que te permite ejecutar Kubernetes localmente en tu máquina. Soporta todas las características de Kubernetes y es una excelente opción para principiantes que quieren una experiencia completa de Kubernetes en su máquina local.

- **[K3s](https://k3s.io/)**: Distribución ligera de Kubernetes por Rancher Labs. K3s es una instalación simplificada y mínima de Kubernetes que funciona bien para desarrollo local y pruebas, particularmente en dispositivos de borde o entornos de pocos recursos.
