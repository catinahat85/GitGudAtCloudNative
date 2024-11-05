# Optimización de Mi Despliegue en Kubernetes

Este documento sigue la evolución de mi configuración y flujo de trabajo. Incluye detalles sobre la arquitectura multicloud, gestión de Kubernetes, flujos de trabajo GitOps y más, con un enfoque en eficiencia de costos, seguridad y escalabilidad.

---

## Tabla de Contenidos
- [Configuración Inicial](#configuración-inicial)
- [Desafíos Multicloud](#desafíos-multicloud)
- [Migración a K3s en Hetzner](#migración-a-k3s-en-hetzner)
- [Optimización de Arquitectura](#optimización-de-arquitectura)
- [Refuerzo de Seguridad](#refuerzo-de-seguridad)
- [Añadiendo Linkerd Service Mesh](#añadiendo-linkerd-service-mesh)
- [Rendimiento Global con CloudFront CDN](#rendimiento-global-con-cloudfront-cdn)
- [Pasos Futuros](#pasos-futuros)

---

## Configuración Inicial

Comencé con una página de destino simple, destinada a reunir mis proyectos y materiales de aprendizaje, pero rápidamente quise más control sobre la plataforma. Inicialmente, desplegué:
- **WordPress en un Servicio Gestionado** - Rápidamente reemplazado por **Ghost en AWS** para una experiencia más ligera.
- **Ghost Dockerizado en una VM de AWS** - Ghost servido a través de un proxy inverso Nginx.
- **Kubernetes Multicloud** - Kubernetes gestionado en DigitalOcean, con AWS para cargas de trabajo específicas.

Herramientas Utilizadas:
- **Prometheus** y **Grafana** para monitoreo.
- **K9s** para gestión de Kubernetes en terminal.
- **GitHub y ArgoCD** para despliegues con GitOps.
- **Cloudflare** para DNS y SSL/TLS.

---

## Desafíos Multicloud

![Configuración Inicial](https://beatsinthe.cloud/blog/content/images/2024/10/7CAFD523-BF78-4384-8CDB-DD9F92BEA7A1.jpeg)

### Puntos Problemáticos:
1. **Gestión de Tráfico y Redes** - Manejar conexiones entre AWS y DigitalOcean generaba complejidades de red.
2. **Gestión de Costos** - Los créditos se estaban agotando, y mantener dos proveedores de nube resultaba caro.
3. **Consistencia de Configuración** - Mantener configuraciones consistentes entre nubes añadía sobrecarga operativa.

### Solución:
**Migración a una Nube Única** - Al mover todo a **Hetzner** bajo una configuración de **K3s** autogestionada, simplifiqué y optimicé la gestión.

---

## Migración a K3s en Hetzner

1. **Configuración de K3s en Hetzner** - Instalé K3s en VPS de Hetzner para una mejor gestión de costos.
2. **Reimplementación de Monitoreo** - Utilicé **Prometheus**, **Grafana** y **K9s** para reemplazar la interfaz de DigitalOcean.
3. **Integración con GitOps** - Con GitOps y ArgoCD, la migración fue fluida, con casi cero tiempo de inactividad.

![Configuración Multicloud](https://beatsinthe.cloud/blog/content/images/2024/10/A0BEB0DE-D73E-4704-A989-75FF1835302C.jpeg)

### Beneficios:
- **Reducción de Costos** - La estructura de precios de Hetzner ahorró significativamente mientras brindaba recursos sólidos.
- **Arquitectura Simplificada** - La consolidación de infraestructura redujo latencia de red y errores.

---

## Optimización de Arquitectura

La configuración simplificada eliminó la necesidad de un proxy inverso multicloud, reduciendo considerablemente la latencia y la complejidad de gestión. Esto allanó el camino para:
- **Integración Directa de Ghost** - Ghost alojado dentro del clúster de K3s.
- **Aislamiento por Namespace** - Ghost desplegado en su propio namespace con la reconciliación de ArgoCD desactivada para evitar problemas de redeployment.

![Configuración de Migración](https://beatsinthe.cloud/blog/content/images/2024/10/E44CEACB-8E22-4BFE-ABEA-D57C9AE44A46.jpeg)

### Mejoras Clave:
- **Mejora de Rendimiento** - Menor latencia y tiempos de carga más rápidos.
- **Mejor Observabilidad** - Todos los componentes monitoreados dentro del mismo entorno.

---

## Refuerzo de Seguridad

Con la arquitectura en su lugar, me enfoqué en fortalecer la seguridad:
1. **Firewalls y Detección de Intrusiones** - Desplegué **Falco** para la detección en tiempo real de intrusiones y configuré alertas vía Slack.
2. **2FA para Ghost Admin** - Añadí autenticación de dos factores para un acceso seguro.
3. **Proxy de Cloudflare** - Activé DNS y protección contra DDOS a través de Cloudflare.

![Arquitectura Optimizada](https://beatsinthe.cloud/blog/content/images/2024/10/CDA12ECA-80E8-4A94-B668-3F8BA4287153.jpeg)

### Añadidos Clave:
- **Falco IDS** - Alertas en tiempo real para actividades sospechosas.
- **Controles de Acceso Mejorados** - Medidas de seguridad que aseguraron la preparación para producción.

---

## Añadiendo Linkerd Service Mesh

Para gestionar el tráfico interno, introduje **Linkerd** para la comunicación entre servicios dentro de K3s:
1. **Gestión de Tráfico** - Mejora en el control sobre el tráfico de red y balanceo de carga.
2. **Observabilidad de Red** - La observabilidad de Linkerd potenció los conocimientos más allá de Prometheus/Grafana.

![Configuración de Seguridad](https://beatsinthe.cloud/blog/content/images/2024/10/EA370075-E0D9-4208-BB19-F580181988AF.jpeg)

### ¿Por Qué Linkerd?
- **Ligero y Eficiente** - Linkerd superó a alternativas como Istio y Cilium en uso de recursos y simplicidad.
- **Seguridad Mejorada** - Comunicación cifrada entre servicios y políticas de tráfico refinadas.

---

## Rendimiento Global con CloudFront CDN

Para optimizar el acceso global:
1. **Integración con CloudFront CDN** - Cacheo de archivos estáticos (imágenes, JavaScript, CSS) para un acceso más rápido en todo el mundo.
2. **Reducción de Carga en el Clúster** - Descargar contenido estático disminuyó la carga de trabajo en K3s.

![Implementación de Linkerd](https://beatsinthe.cloud/blog/content/images/2024/10/EA370075-E0D9-4208-BB19-F580181988AF--1--1.jpeg)

### Resultado:
Mejor experiencia de usuario y reducción de latencia para usuarios en todo el mundo.

---

## Pasos Futuros

- **Consolidar Aún Más** - Explorando opciones de alojamiento más económicas con potencia comparable para mayores ahorros.
- **Registro de Contenedores Remoto** - Transición desde DockerHub para una solución gratuita con múltiples repositorios.
- **Escalado con Nuevos Servicios** - Planeando nuevos elementos para el sitio (e.g., e-commerce y foro comunitario) a medida que el proyecto crece.

---

Este viaje destaca el proceso iterativo de refinar la infraestructura en la nube, dominar herramientas cloud-native y equilibrar el rendimiento con limitaciones presupuestarias. ¡Estén atentos para futuras actualizaciones!



