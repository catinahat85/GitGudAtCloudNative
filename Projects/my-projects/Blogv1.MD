# Desplegando Mi Sitio en Kubernetes con GitHub Actions y Argo CD

Quería un lugar para reunir todo: mis audios para estudiar, mis despliegues, mis libros, y este repositorio de recursos educativos. Así que hice **[el repositorio](https://github.com/catinahat85/CloudFiLive)** para mi sitio principal, **[Beatsinthe.cloud](http://Beatsinthe.cloud)** público, para que puedas observar o incluso hacer un fork. Este repositorio contiene el código fuente y la configuración para mi sitio web, desplegado en un clúster de Kubernetes alojado en DigitalOcean. El despliegue se automatiza usando **GitHub Actions** y **Argo CD**, lo que asegura que los cambios realizados en el repositorio se reflejan en el entorno en vivo sin intervención manual.

## Descripción General

Configuré el **pipeline CI/CD** para construir y desplegar automáticamente cambios en mi sitio. Las herramientas que usé en este proceso son:

- **GitHub Actions**: Utilizado para construir la imagen de Docker y subirla a DockerHub cuando se realizan cambios en el repositorio.
- ~**Flux Image Reflector**: Observa las imágenes de DockerHub y actualiza automáticamente el despliegue en Kubernetes para reflejar los cambios.~
- **Argo CD Core**: Cambié de Flux a Argo ya que es más fácil de configurar y usar, tiene una interfaz más limpia y ofrece monitoreo intuitivo en tiempo real de los despliegues en comparación con Flux. Es ideal para quienes quieren resultados rápidos con menos complicaciones.
- **Docker**: Conteneriza la aplicación para su despliegue en Kubernetes.
- **Kubernetes**: Orquesta el despliegue, escalado y gestión de la aplicación contenerizada.

## Estructura del Proyecto

Aquí tienes una descripción de los archivos y directorios importantes en este repositorio:

- `.github/workflows/Update docker-image.yml`: El flujo de trabajo de GitHub Actions que automatiza el proceso de construcción y subida de imágenes de Docker.
- `./deployment.yaml`: Define el despliegue de Kubernetes para la aplicación.
- `service.yaml`: Configura el servicio de Kubernetes para exponer la aplicación.
- `kustomization.yaml`: Administra la personalización de los manifiestos de Kubernetes.
- `Dockerfile`: Describe cómo se construye la imagen de Docker.

## Descripción del Flujo de Trabajo

### 1. GitHub Actions para CI

Cada vez que realizo cambios en el repositorio, GitHub Actions desencadena un flujo de trabajo que:

- **Construye la imagen de Docker** usando el `Dockerfile`.
- **Sube la imagen actualizada** a mi cuenta de DockerHub.

Esto automatiza el proceso de creación de imágenes, asegurando que la última versión del sitio esté siempre disponible.

### 2. Argo CD para Despliegue Continuo

Argo CD monitorea continuamente mi repositorio de DockerHub en busca de cambios en la imagen de la aplicación. Cuando se detecta una nueva imagen, Argo:

- **Actualiza el despliegue en Kubernetes** con la nueva imagen.
- **Realiza el despliegue** reemplazando el despliegue anterior con el nuevo, asegurando cero tiempo de inactividad durante la actualización.

### 3. Kubernetes

Kubernetes maneja el despliegue y el escalado de la aplicación contenerizada. Los despliegues y servicios de la aplicación se definen en los archivos `deployment.yaml` y `service.yaml`, que determinan cómo se ejecuta el sitio y cómo se expone a Internet.

## Cómo Funciona

Aquí tienes una visión general de cómo funciona la automatización:

1. Realizo cambios en el repositorio (ej., modificando `index.html` o `Dockerfile`).
2. GitHub Actions construye y sube la nueva imagen de Docker a DockerHub.
3. Argo detecta la nueva imagen en DockerHub y actualiza el despliegue en Kubernetes.
4. Kubernetes despliega la actualización sin ningún tiempo de inactividad.

## Herramientas Utilizadas

- **GitHub Actions**: Para automatizar el proceso CI (construcción y subida de imagen Docker).
- **Argo**: Para automatizar el proceso CD (monitoreo y actualización de despliegues en Kubernetes).
- **Docker**: Para contenerizar la aplicación nginx.

- **Kubernetes**: Para orquestar la aplicación contenerizada en un entorno en la nube.
- **DigitalOcean**: Como proveedor de nube para alojar el clúster de Kubernetes.

## ¿Por Qué Esta Configuración?

Esta configuración proporciona un pipeline CI/CD totalmente automatizado para desplegar mi sitio. Usar GitHub Actions para CI y Argo para CD asegura que puedo enfocarme en lo divertido (escribir código HTML, ¡hurra!), mientras el proceso de despliegue se maneja de manera automática y sin intervención. También porque no quiero mucho mantenimiento y quería presumir. También porque soy un poco perezoso y presumido.

---

Ahora que sabes qué y cómo lo hice, algunas reflexiones y puntos clave:

# Cosas Importantes a Saber Sobre DockerHub
Si estás considerando usar DockerHub para producción, tal vez piénsalo dos veces.

Los usuarios de la versión gratuita están sujetos a límites de extracción:
- **Usuarios anónimos**: Hasta **100 extracciones cada 6 horas**.
- **Usuarios autenticados**: Hasta **200 extracciones cada 6 horas**.
Esto puede afectar a entornos de producción que dependen de DockerHub para extracciones frecuentes de imágenes, especialmente en despliegues de mayor tamaño.

DockerHub elimina automáticamente **imágenes inactivas** que no se han extraído o actualizado en **6 meses** en la versión gratuita. Debes mantenerte activo para evitar perder imágenes, lo cual puede ser problemático si usas imágenes antiguas para despliegues futuros.

Las imágenes públicas pueden ser accedidas por cualquiera, lo que podría exponer tu entorno a posibles vulnerabilidades si no se mantienen adecuadamente. 

# ¿Por Qué Mi Configuración Es Realmente Excesiva?
Algunas razones por las que la configuración que implementé podría considerarse excesiva para este proyecto:

## Despliegue de Un Solo Nodo
- Ejecutar un **clúster de Kubernetes** para un sitio de un solo nodo puede ser excesivo. Una solución más sencilla, como usar Docker directamente en una máquina virtual (VM), podría lograr el mismo resultado con menos complejidad.

# Si Estás Buscando No Gastar Mucho en Kubernetes
Si buscas formas económicas (es decir, BARATAS) para ejecutar Kubernetes, considera estas opciones:

1. **DigitalOcean/Linode/Vultr/Civo**  
   Tienen servicios de Kubernetes gestionados y de bajo costo. No recibo ingresos de ellos, pero son económicos. Eso sí, cobran por los balanceadores de carga. Y los necesitas.

2. **K3s, Minikube o MicroK8s**  
   Distribución ligera de Kubernetes, ideal para dispositivos de borde o entornos en la nube.

3. **Autogestionado en Máquinas Virtuales en la Nube**  
   Usa VMs en la nube de AWS, GCP, Azure, OVH, Civo y DigitalOcean.

4. **Kubernetes en Docker Desktop o OpenShift OKD**  
   Docker Desktop tiene una función que incluye Kubectl para ejecutar un pequeño clúster localmente. Nunca he probado Openshift, pero he oído cosas positivas.

Si deseas hacer un proyecto para presumir, hacerlo en la nube es el camino.

---

Como dije antes, el punto de esto era demostrar mis habilidades, que sé de lo que hablo y mostrar mi trabajo.

- En 2020, hacía sitios en Blogger y WordPress.
- En 2021, usaba AWS S3 para hacer un objeto público y usar la IP externa como sitio.
- En 2022, usaba nginx y apache para gestionar mis propios servidores en una VM con múltiples sitios.
- En 2023, reduje el uso de recursos desplegando esos servidores con Docker.
- En 2024, estoy completamente en la nube multicloud, usando Kubernetes, con alta disponibilidad y CI/CD automatizado. Todo esto por menos de $24 al mes.

**Próximo paso: trabajar en monitoreo y observabilidad.**
