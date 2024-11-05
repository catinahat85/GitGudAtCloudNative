# Recursos de Aprendizaje para Kubernetes

Mi filosofía es esta: La orquestación de contenedores llegó para quedarse. Se está volviendo ubicua a un ritmo acelerado, y el auge de la IA solo acelerará esto. Conocer "la nube" es solo el comienzo, así que incluso tener un conocimiento básico de tecnologías Cloud Native es imprescindible si deseas iniciar tu carrera como "Ingeniero de la Nube" (que, hoy en día, es más un término amplio que un rol específico).

## ¿Entonces, Qué es "Cloud Native"?
En resumen, es tecnología diseñada para aprovechar los entornos de computación en la nube, sus capacidades de escalabilidad, potencia de cálculo y su naturaleza descentralizada.

Según la **[CNCF o Fundación de Computación Nativa de la Nube](https://www.cncf.io)**, la organización líder en el desarrollo de tecnologías Cloud Native, Cloud Native se define como:
"Las prácticas Cloud Native permiten a las organizaciones desarrollar, construir y desplegar cargas de trabajo en entornos de computación (nube pública, privada, híbrida) para satisfacer sus necesidades organizacionales a escala de una manera programática y repetible. Se caracteriza por sistemas desacoplados que interactúan de manera segura, resiliente, manejable, sostenible y observable. Las tecnologías y arquitecturas Cloud Native suelen consistir en una combinación de contenedores, mallas de servicio, multi-tenencia, microservicios, infraestructura inmutable, computación sin servidor y APIs declarativas."

Piensa en lo siguiente:
- Orquestación de contenedores (Kubernetes, Google Borg, Docker Borg, Docker Swarm, Openshift)
- Contenedores (Docker, etc.)
- Lagos de Datos (Delta Lake)
- Mallas de Servicios
- Microservicios
- Computación sin Servidor
- Puertas de Enlace de API
- Herramientas de Observación y Monitoreo

¿Te sientes intimidado? No lo estés. Paso a paso. Yo también estuve aprendiendo una vez, y aún lo estoy. Este espacio está destinado a compartir mi recorrido, pasado y en curso. Así que no estás solo.

## Índice
1. [Empezar con Docker](#empezar-con-docker)
2. [Mis Apuntes de Estudio, Perfectos para KCNA](#mis-apuntes-de-estudio)
3. [Cursos Introductorios de Kubernetes](#cursos-introductorios-de-kubernetes)
4. [Teoría de Kubernetes en Video](#teoria-de-kubernetes-en-video)
5. [Recursos de Aprendizaje Práctico de Kubernetes](#recursos-de-aprendizaje-practico-de-kubernetes)
6. [¿Instalar Kubernetes Localmente?](#instalar-kubernetes-localmente)

---

## Empezar con Docker
Si eres nuevo en la contenedorización, estos recursos te ayudarán a comenzar con Docker.

- **[Despliega Aplicaciones Cloud Native Usando Azure Container Apps](https://learn.microsoft.com/en-us/credentials/applied-skills/deploy-cloud-native-apps-using-azure-container-apps/)**: Módulo de Microsoft Learn que enseña cómo desplegar aplicaciones nativas de la nube utilizando Azure Container Apps, ideal para entusiastas de Azure.

- **[Fundamentos de Docker - Cognitive Class](https://cognitiveclass.ai/courses/docker-essentials)**: Curso de nivel principiante sobre Docker, que cubre conceptos básicos de contenedores, cómo trabajar con imágenes y contenedores de Docker, y administrar Docker Hub.

---

## Mis Apuntes de Estudio
- **[Apuntes de Estudio](https://github.com/catinahat85/GitGudAtCloudNative/blob/main/learning-resources/kubernetes/Kubernetes%20Cloud%20Native%20Study%20Guide.pdf)**: Tomados de varias fuentes, incluyendo la documentación oficial, han sido útiles cuando he estado atascado. Si estás considerando obtener tu KCNA, son excelentes para revisar.
- **[Lofi Study Cram](https://www.youtube.com/watch?v=ipDBBMcSJDM&ab_channel=CloudFiBeats)**: Una versión narrada y relajante de los apuntes de estudio, creada con AWS Polly, sobre mis propios beats de Lofi para que puedas escuchar mientras haces ejercicio, conduces o trabajas. A mí me funciona, así que pensé en compartirlo.

---

## Cursos Introductorios de Kubernetes
¿No estás seguro de qué es Kubernetes (K8s)? Comienza aquí con estos cursos básicos.

- **[Introducción a Kubernetes de Linux Foundation](https://training.linuxfoundation.org/training/introduction-to-kubernetes/)**: Curso introductorio oficial de la Fundación Linux.
  
- **[Introducción a Kubernetes de Linux Foundation en EdX](https://www.edx.org/learn/kubernetes/the-linux-foundation-introduction-to-kubernetes)**: El mismo curso oficial, disponible en EdX.

- **[Academia de Civo](https://www.civo.com/academy)**: Cursos gratuitos de tecnología Kubernetes y Cloud Native, que cubren los conceptos básicos del desarrollo Cloud Native, contenedores y Kubernetes.

---

## Teoría de Kubernetes en Video
Algunos videos recomendados que explican conceptos de Kubernetes, casos de uso, etc.

- **[Aprende Kubernetes - KodeKloud](https://youtu.be/XuSQU5Grv1g?si=cRYIMRJ74BC4FiT0)**: Una introducción completa y amigable para principiantes sobre Kubernetes, presentada por KodeKloud, que cubre los conceptos básicos y demostraciones prácticas.

- **[Tutorial de Kubernetes - Techworld con Nana](https://youtu.be/X48VuDVv0do?si=WtiwUqi1CHDnJum_)**: Otro excelente tutorial de Kubernetes de Techworld con Nana, que ofrece explicaciones claras y ejemplos prácticos.

---

## Recursos de Aprendizaje Práctico de Kubernetes
Aquí encontrarás recursos que te ayudarán a practicar Kubernetes con laboratorios y entornos prácticos.

- **[Laboratorio de Kubernetes de Google Cloud](https://www.cloudskillsboost.google/course_templates/783)**: Laboratorio práctico de Kubernetes ofrecido por Google Cloud.

- **[KillerCoda](https://killercoda.com/)**: Una plataforma de aprendizaje interactivo para Kubernetes con escenarios reales.

- **[Killer Shell](https://killer.sh/)**: Entorno de práctica para Kubernetes, ideal para preparar los exámenes CKA/CKAD.

- **[Play with K8s](https://labs.play-with-k8s.com/)**: Herramienta gratuita que te permite crear clústeres de Kubernetes en tu navegador y experimentar.

- **[Tutoriales del Servicio de Kubernetes de IBM](https://www.ibm.com/products/kubernetes-service/kubernetes-tutorials)**: Colección de tutoriales de Kubernetes de IBM para ayudarte a comenzar a gestionar aplicaciones en clústeres de Kubernetes usando el Servicio de Kubernetes de IBM.

- **[Comienza con Kubernetes](https://collabnix.github.io/kubelabs/)**: Una increíble lista de laboratorios y tutoriales de Kubernetes.

---

## Instalar Kubernetes Localmente
¿Listo para trabajar con K8s localmente? Aquí tienes algunas formas de hacerlo. Docker Desktop y Multipass probablemente sean las opciones más fáciles, ¡pero si te animas, lanza Minikube o K3s!

- **[MicroK8s con Multipass](https://microk8s.io/docs/install-multipass)**: MicroK8s es una instalación de Kubernetes pequeña, rápida y segura de Canonical, ideal para configuraciones locales. Multipass crea máquinas virtuales aisladas para ejecutar MicroK8s, simplificando el proceso de crear clústeres de Kubernetes en tu máquina local.

- **[Kubernetes en Docker Desktop](https://docs.docker.com/desktop/kubernetes/)**: Docker Desktop incluye una forma sencilla de habilitar un clúster de Kubernetes de un solo nodo en tu máquina local. Si ya estás utilizando Docker para desarrollo de contenedores, esta es una forma fácil de integrar Kubernetes en tu flujo de trabajo.

- **[Minikube](https://minikube.sigs.k8s.io/docs/)**: Minikube es una herramienta que te permite ejecutar Kubernetes localmente en tu máquina. Soporta todas las características de Kubernetes y es una excelente opción para principiantes que desean una experiencia completa de Kubernetes en su máquina local.

- **[K3s](https://k3s.io/)**: Distribución ligera de Kubernetes de Rancher Labs. K3s es una instalación simplificada y mínima de Kubernetes que funciona bien para desarrollo y pruebas locales, particularmente en dispositivos de borde o entornos con pocos recursos.

