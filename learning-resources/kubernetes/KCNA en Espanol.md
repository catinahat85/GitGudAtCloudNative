Guía de estudio sobre Kubernetes y Cloud Native

Componentes del plano de control
Administre el estado general del clúster:
servidor kube-api
El servidor de componentes principal que expone la API HTTP de Kubernetes
etcd
Almacén de valores clave coherente y de alta disponibilidad para todos los datos de los servidores de API En Kubernetes, etcd es la «fuente de la verdad» y almacena todos los datos de estado y configuración del clúster, incluidos los objetos, los secretos y los ajustes de configuración.
kube-scheduler
Busca los pods que aún no estén enlazados a un nodo y asigna cada pod a un nodo adecuado. El kube-scheduler se activa para asignar un pod a un nodo cuando el pod se crea sin un nombre de nodo específico, y determina cuál es el mejor nodo en función de las necesidades y restricciones de recursos. 
kube-controller-manager
Ejecuta controladores para implementar el comportamiento de la API de Kubernetes.
administrador de controladores en la nube (opcional)
Se integra con los proveedores de nube subyacentes.
Componentes del nodo
Ejecute en todos los nodos, mantenga los pods en ejecución y proporcione el entorno de ejecución de Kubernetes:
kubelet
Garantiza que los pods estén funcionando, incluidos sus contenedores, y es el principal responsable de garantizar que los contenedores funcionen según lo definido en las especificaciones de los pods. En Kubernetes, el componente de un nodo responsable de ejecutar los contenedores, tal y como se especifica en las definiciones de los pods, es el kubelet. El kubelet monitorea continuamente el estado del nodo y se asegura de que los contenedores descritos en las especificaciones del pod funcionen según lo esperado. Se comunica con el tiempo de ejecución del contenedor (por ejemplo, Docker o containerd) para lanzar y administrar los contenedores.
kube-proxy (opcional)
Responsable de enrutar el tráfico de los servicios y administrar las reglas de IP. Mantiene las reglas de red en los nodos para implementar los servicios.
Tiempo de ejecución del contenedor
Software responsable de ejecutar los contenedores. Este elemento enlaza con un proyecto o producto de terceros que no forma parte de Kubernetes en sí. Es posible que su clúster necesite software adicional en cada nodo; por ejemplo, también puede ejecutar systemd en un nodo de Linux para supervisar los componentes locales.
Complementos
DNS
Complemento para la resolución de DNS en todo el clúster
Interfaz de usuario web (panel de control)
Complemento para la administración de clústeres a través de una interfaz web
Monitorización de recursos de contenedores
Complemento para recopilar y almacenar las métricas de los contenedores
Registro a nivel de clúster
Complemento para guardar los registros de los contenedores en un almacén de registros central
Cumplimiento de la Iniciativa de Contenedores Abiertos (OCI)
RunC es el motor de ejecución nativo que cumple con los estándares de la Open Container Initiative (OCI) y sirve como implementación de referencia para sus estándares. Garantiza la compatibilidad de los contenedores en varias plataformas. 
Ejecución de aplicaciones sin estado en Kubernetes
La implementación es el objeto de API recomendado para ejecutar aplicaciones escalables y sin estado en un clúster de Kubernetes. Gestiona el estado deseado de las aplicaciones y gestiona las actualizaciones y el escalado de forma eficiente.
Ejecución de CronJob en Kubernetes
Controlador CronJob: en Kubernetes, el controlador CronJob es responsable de crear un trabajo a una hora programada, lo que a su vez crea un pod para ejecutar las tareas. El pod se ejecuta y completa las tareas asignadas de acuerdo con el cronograma.
El papel de Kubelet en Kubernetes
Kubelet es un componente esencial de Kubernetes. Se ejecuta en cada nodo del clúster y garantiza que los contenedores se ejecuten dentro de los Pods según lo previsto. El kubelet es responsable de ejecutar los contenedores en un nodo de acuerdo con las especificaciones de los pods.
Tipos de servicio de Kubernetes
Ingress no se considera un tipo de servicio. Los servicios de Kubernetes incluyen 
 ClusterIP, 
 Puerto de nodo, 
 LoadBalancer, y 
 ExternalName, que expone las aplicaciones que se encuentran dentro o fuera del clúster.
Estándar de comunicación Kubelet
Interfaz de ejecución de contenedores (CRI): Kubelet usa la CRI para comunicarse con los tiempos de ejecución de contenedores, como containerd o CRI-O.
Funcionalidad de C-groups
Los Cgroups (grupos de control) permiten limitar los recursos dentro de un sistema, lo que garantiza que los contenedores no superen la CPU, la memoria u otros recursos asignados.
Escalar aplicaciones en la nube
El escalado horizontal es el método más común para escalar las aplicaciones en la nube, donde se agregan más réplicas de una aplicación o un servidor para gestionar la carga adicional.
Ventajas de los microservicios nativos de la nube
Los microservicios ofrecen una mayor flexibilidad y escalabilidad en comparación con las aplicaciones monolíticas, lo que facilita la escalabilidad y la realización de actualizaciones en componentes específicos sin afectar a todo el sistema.
Escalado vertical
El escalado vertical implica la asignación de recursos adicionales (como memoria o CPU) a las instancias existentes de una aplicación para aumentar su capacidad.
Componentes del plano de control de Kubernetes
kube-proxy no forma parte del plano de control, pero funciona como un proxy de red en cada nodo. Los componentes del plano de control incluyen kube-apiserver, kube-scheduler y etcd.
Factores en la programación de nodos
Kubernetes tiene en cuenta los requisitos de recursos al seleccionar un nodo para programar un pod. Se tienen en cuenta factores como la CPU, la memoria y las reglas de afinidad.
Uso de etcd en Kubernetes
etcd es el almacenamiento de objetos de fondo de la API de Kubernetes, que almacena todos los datos del clúster, incluidas las configuraciones, los secretos y la información de estado. En Kubernetes, etcd es la «fuente de la verdad», ya que almacena todos los datos de estado y configuración del clúster, incluidos los objetos, los secretos y los ajustes de configuración.
Tiempos de ejecución de contenedores con Kubernetes
Kubernetes admite varios tiempos de ejecución de contenedores, como CRI-O, containerd y el ahora obsoleto Dockershim.
Creación de trabajos en Kubernetes
Un recurso de CronJob se usa para crear trabajos de Kubernetes a intervalos programados, por ejemplo, cada hora o todos los días.
Características de los StatefulSets
Los StatefulSets ofrecen una implementación y un escalado ordenados y ordenados, y se utilizan a menudo para aplicaciones con estado. También confían en los servicios independientes para mantener una identidad de red estable.
Agregar nuevos tipos de recursos
Las definiciones de recursos personalizadas (CRD) permiten a los usuarios ampliar la API de Kubernetes añadiendo nuevos tipos de recursos específicos para sus aplicaciones.
Escalado horizontal
El escalado horizontal es el proceso de agregar réplicas adicionales de una aplicación o un servidor para gestionar más tráfico o carga.
Edición de recursos en Kubernetes
kubectl edit es el comando que se usa para modificar los recursos directamente en el servidor de Kubernetes.
Modelo de computación sin servidor
El modelo sin servidor es un modelo de computación en la nube en el que el aprovisionamiento y la administración de la infraestructura no recaen en el usuario. Los desarrolladores se centran únicamente en el código.
Ejecutar pods en nodos específicos
Un DaemonSet garantiza que un pod se ejecute en todos o en algunos nodos específicos, por ejemplo, para supervisar o registrar aplicaciones.
Construcciones de pods de Kubernetes
Un pod de Kubernetes contiene uno o más contenedores, lo que lo convierte en la unidad desplegable más pequeña de Kubernetes.
La unidad más pequeña de Kubernetes
El pod es la unidad más pequeña posible en Kubernetes que puede ejecutar un contenedor.
Obtención de documentación con kubectl
kubectl explain proporciona documentación detallada para un tipo de recurso específico directamente desde la línea de comandos.
Escalador automático de clústeres
Ajusta automáticamente la cantidad de nodos de un clúster en función de la demanda de recursos.
Protección de secretos
Kubernetes almacena los secretos como valores codificados en Base64, lo que garantiza la confidencialidad básica. Los datos no se cifran, sino que se codifican mediante base64, que es un mecanismo de codificación reversible simple. Kubernetes almacena los secretos en etcd, el almacén de valores clave del clúster, que normalmente se cifra en reposo cuando se configura correctamente.
Proxy de Kube
Gestiona el reenvío de la red a los puntos finales de servicio correctos en un clúster de Kubernetes. En Kubernetes, un punto final se usa principalmente para representar las direcciones IP y los puertos de los pods que están asociados a un servicio. Realiza un seguimiento de las ubicaciones de red de los pods reales que respaldan el servicio, lo que permite la comunicación entre los servicios y los pods.
Programación dinámica
Kubernetes programa las cargas de trabajo de forma dinámica en función de la disponibilidad de los recursos y las características de los nodos.
Helm
Helm, un administrador de paquetes para Kubernetes, simplifica la implementación y la administración de las aplicaciones.
Herramientas de GitOps
Herramientas como Argo CD y Flux comparan de forma continua el estado deseado en Git con el estado real de producción, teniendo en cuenta las diferencias.
Definición de recursos personalizada (CRD)
Una forma de ampliar la API de Kubernetes mediante la definición de nuevos tipos de recursos. Los CRD permiten crear objetos de recursos personalizados específicos para una aplicación, lo que amplía la funcionalidad de Kubernetes sin alterar la API principal. Se administran mediante comandos estándar de kubectl.
Interfaz Service Mesh (SMI)
Un estándar común para las mallas de servicios, que ayuda a la comunicación entre microservicios. En el contexto de las aplicaciones nativas de la nube, la interfaz Service Mesh (SMI) se reconoce como la especificación de interfaz estandarizada para las mallas de servicios. Entre las principales características de las interfaces de malla de servicio se incluyen las siguientes:
 Proporciona una API común para las mallas de servicios en Kubernetes.
 Define las interfaces de administración del tráfico, seguridad y observabilidad en diferentes implementaciones de redes de servicios.


Entrada
Administra el acceso externo a los servicios dentro de un clúster de Kubernetes al exponer las rutas HTTP a los servicios. Ingress dirige el tráfico HTTP y HTTPS externo a los servicios del clúster
Descubrimiento de servicios
Ayuda a que las aplicaciones y los microservicios se localicen entre sí en una red, algo crucial para las aplicaciones nativas de la nube.
Arquitectura de Kubernetes
Componentes del nodo maestro:
kube-apiserver: administra las solicitudes de API y sirve como puerta de entrada al clúster.
etcd: almacena el estado del clúster de Kubernetes. En Kubernetes, etcd es la «fuente de la verdad» y almacena todos los datos de configuración y estado del clúster, incluidos los objetos, los secretos y los ajustes de configuración.
kube-scheduler: decide en qué nodos se ejecutan nuevos pods en función de la disponibilidad de recursos. El kube-scheduler asigna un pod a un nodo cuando se crea sin un nodeName, en función de los requisitos y las restricciones de los recursos.
kube-controller-manager: administra los controladores principales, como el Node Controller, el Replication Controller y otros.
Componentes del nodo de trabajo:
kubelet: garantiza que los contenedores se ejecuten en Pods.
kube-proxy: gestiona el proxy de red para los servicios y dirige el tráfico al contenedor apropiado.
Tiempo de ejecución del contenedor: software responsable de ejecutar los contenedores, por ejemplo, containerd, CRI-O.
Redes de Kubernetes
Tipos de servicio:
ClusterIP: expone los servicios solo dentro del clúster.
NodePort: expone los servicios en un puerto estático en la IP de cada nodo.
LoadBalancer: expone los servicios de forma externa mediante el balanceador de cargas de un proveedor de nube.
ExternalName: asigna un servicio a un nombre DNS externo.
Ingress: proporciona acceso externo a los servicios a través de HTTP y HTTPS. Gestiona el enrutamiento en función de las rutas URL y los nombres de host.
Políticas de red: define cómo los pods pueden comunicarse entre sí y con otros puntos finales de la red. En Kubernetes, las políticas de red son aditivas. Esto significa que cuando se aplican varias políticas de red al mismo conjunto de módulos, las políticas se combinan (o se intersecan) y el tráfico solo está permitido si cumple con las reglas de todas las políticas aplicables. Básicamente, cada política añade restricciones y solo se permitirá el tráfico permitido de forma explícita en todas las políticas.
Objetos de Kubernetes
Pod: la unidad desplegable más pequeña, que contiene uno o más contenedores.
Implementación: administra los pods sin estado, lo que permite actualizarlos y escalarlos de forma continua.
ReplicaSet: garantiza que se esté ejecutando una cantidad específica de pods en un momento dado.
DaemonSet: garantiza que un pod se ejecute en todos (o algunos) de los nodos del clúster.
StatefulSet: administra las aplicaciones con estado, lo que garantiza que los pods tengan identidades estables.
Job/CronJob: ejecuta los pods hasta completarlos. CronJobs se ejecuta de forma programada.
PersistentVolume (PV) y PersistentVolumeClaim (PVC): recursos de almacenamiento abstractos en Kubernetes.
Orquestación de contenedores
Programación de contenedores: Kubernetes usa el planificador para decidir qué nodos deben ejecutarse en función de los requisitos y restricciones de recursos.
Afinidad o antiafinidad: define reglas para determinar cómo se distribuyen los pods entre los nodos (por ejemplo, colocar ciertos pods juntos o separados).
Pertinencias y tolerancias: se utilizan para impedir o permitir que se programen pods en determinados nodos. Las contaminaciones se establecen en los nodos y los pods deben tener una tolerancia equivalente para poder programarse en nodos contaminados.
Conceptos nativos de la nube
Aplicación de 12 factores: conjunto de directrices para ayudar a diseñar aplicaciones nativas de la nube escalables y fáciles de mantener, incluida la contenedorización, la configuración del entorno y la gestión de dependencias.
Los cuatro pilares de la arquitectura nativa de la nube son:
1. Microservicios: descomposición de las aplicaciones en servicios independientes y poco acoplados que se pueden desarrollar e implementar por separado.
2. Contenedores: empaquetan las aplicaciones y sus dependencias en unidades livianas y portátiles que pueden funcionar de manera uniforme en varios entornos.
3. DevOps: fomentar la colaboración entre los equipos de desarrollo y operaciones, haciendo hincapié en la automatización y mejorando el proceso de entrega.
4. Integración continua/implementación continua (CI/CD): automatización de la integración, las pruebas y la implementación del código para permitir lanzamientos de software rápidos y confiables.
Microservicios: un estilo de arquitectura en el que las aplicaciones se componen de servicios pequeños e independientes que se comunican a través de API.
Service Mesh: una capa de infraestructura dedicada para administrar la comunicación por microservicios. Una malla de servicios facilita la distribución y replicación de datos entre los servicios al:
 División del tráfico: dirige el tráfico a diferentes versiones del servicio para lograr actualizaciones graduales y lograr la coherencia de los datos.
 Equilibrio de carga global: distribuye las solicitudes entre las regiones para lograr una alta disponibilidad y replicación.
 Comunicación entre servicios: garantiza una comunicación segura y confiable para la sincronización de datos.
 Además, proporciona administración del tráfico, detección de servicios, seguridad (TLS mutuo, cifrado), observabilidad (monitoreo, registro, rastreo) y resiliencia (reintentos, tiempos de espera, interrupciones del circuito).
Entre las herramientas de red de servicios más comunes se incluyen Istio y Linkerd. Por lo general, una malla de servicios incluye:
1. Proxy: los proxies de Sidecar (por ejemplo, Envoy) administran el tráfico de cada servicio.
2. Plano de control: configura y administra los proxies, gestionando las políticas de tráfico y la seguridad (por ejemplo, Istio).
3. Plano de datos: los proxies gestionan el tráfico de red entre los servicios.
4. Seguridad: garantiza el cifrado (mTLS), la autenticación y la autorización.
5. Observabilidad: recopila métricas, rastreos y registros para su monitoreo.
6. Administración del tráfico: administra el equilibrio de carga, los reintentos y el enrutamiento del tráfico.
DevOps: una práctica cultural y técnica que une a los equipos de desarrollo y operaciones para automatizar y optimizar la entrega de software.
CI/CD: La integración continua (CI) y la entrega e implementación continuas (CD) son prácticas esenciales para realizar cambios de código de manera frecuente y confiable. En el proceso tradicional de CI/CD:
1. Integración continua (CI): implica automatizar la integración de los cambios de código de varios colaboradores, por lo general mediante procesos de creación y prueba automatizados.
2. Despliegue continuo (CD): implementa automáticamente todos los cambios que pasan por la fase de prueba hasta la fase de producción sin intervención manual. Este flujo de trabajo hace hincapié en que, una vez que el código se ha integrado y probado, se implementa directamente en el entorno de producción.
Esto contrasta con la entrega continua, en la que el código se prepara automáticamente para su implementación en producción, pero es posible que aún se requiera una aprobación manual para su lanzamiento real.
Infraestructura como código (IaC): administración de la infraestructura mediante archivos de configuración legibles por máquina en lugar de mediante una configuración de hardware físico.
Los servicios independientes de Kubernetes no equilibran la carga, sino que proporcionan acceso directo a las IP de cada pod, lo que permite la comunicación con instancias de pod específicas. Es compatible con la detección de servicios y con nombres DNS estables para los pods de StatefulSet, y es ideal para cargas de trabajo con estado continuo, como las bases de datos, que necesitan un almacenamiento persistente e identidades de red coherentes. Para lograr una nomenclatura de DNS uniforme para los pods administrados por un StatefulSet en Kubernetes, debes usar un servicio independiente. Esto permite que cada pod tenga una entrada de DNS estable, normalmente con el formato pod-name.service-name.namespace.svc.cluster.local, lo que garantiza identidades de red coherentes para los pods de StatefulSet.
Observabilidad en Kubernetes
Registros: consulta los registros de los pods en ejecución mediante los registros de kubectl. Para ver los registros en tiempo real, usa la opción -f.
Métricas: recopila datos de rendimiento con herramientas como Prometheus o el servidor de métricas de Kubernetes.
Supervisión: se utilizan herramientas como Grafana, Prometheus y Jaeger para supervisar y rastrear las cargas de trabajo de Kubernetes.
Prometheus: una solución de monitoreo de código abierto que recopila y almacena métricas como datos de series temporales, con un potente lenguaje de consulta para el análisis de datos. Se usa comúnmente junto con Grafana para visualizar las métricas. Prometheus admite cuatro tipos de métricas:
Contador: acumulativo, solo aumenta (p. ej., el recuento de solicitudes).
Indicador: puede aumentar o disminuir (por ejemplo, el uso de memoria).
Histograma: registra las observaciones en grupos (por ejemplo, la duración de las solicitudes).
Resumen: es similar al histograma, pero también proporciona cuantiles (por ejemplo, la mediana de la duración de las solicitudes).
Grafana: una aplicación web versátil de análisis y visualización de código abierto que admite varias fuentes de datos, incluido Prometheus. Es conocida por su capacidad para crear paneles detallados que proporcionan información sobre las métricas y los registros
Fluentd: un recopilador de datos de código abierto diseñado para una capa de registro unificada, que permite integrar la recopilación y el consumo de datos para mejorar la comprensión de los datos. Su vasto ecosistema de complementos admite conexiones de datos con múltiples fuentes y destinos
KubeCost: se centra en la administración de costos de Kubernetes, lo que permite a los equipos monitorear, analizar y optimizar sus gastos en Kubernetes de manera eficiente.
OpenTracing y OpenTelemetry se centran principalmente en la capa de aplicación de una arquitectura de software para la supervisión y la observabilidad.
 Estas herramientas se centran en el rastreo, las métricas y el registro distribuidos dentro de las aplicaciones, lo que permite rastrear las solicitudes a medida que pasan por los diferentes servicios y componentes de una arquitectura de microservicios.
 Al instrumentar la capa de aplicación, proporcionan información sobre el rendimiento, la latencia y las dependencias entre los servicios, lo que ayuda a los desarrolladores a supervisar y solucionar problemas en sistemas distribuidos complejos.


________________


Service Mesh
Las mallas de servicios ofrecen una capa de infraestructura sólida que facilita la comunicación segura y confiable de servicio a servicio dentro de las arquitecturas de microservicios, lo que mejora la observabilidad, la confiabilidad y la seguridad.
Cilium: utiliza la tecnología eBPF para proporcionar funciones de seguridad avanzadas, conectividad de red y equilibrio de carga para los clústeres de Kubernetes. Es fundamental para proteger la comunicación de la red y hacer cumplir las políticas de seguridad
Linkerd: una red de servicios ligera y de alto rendimiento que simplifica la comunicación entre servicios con observabilidad, rastreo y seguridad integrados, lo que requiere una configuración mínima
Istio: ofrece una solución integral de red de servicios que permite un control detallado de la comunicación entre servicios con funciones como la comunicación segura entre servicios, la gestión del tráfico y una amplia capacidad de observación. Istio usa Envoy como su proxy de servicio predeterminado
Envoy: Diseñado para aplicaciones modernas nativas de la nube, este proxy periférico y de servicio es la base de varias implementaciones de redes de servicios, incluida Istio, que proporciona detección dinámica de servicios, equilibrio de carga y terminación de TLS
Tiempo de ejecución y ejecución del contenedor
En esta sección se describen las herramientas esenciales para la administración de contenedores y se destaca la distinción entre los tiempos de ejecución de los contenedores y las soluciones de administración de Kubernetes.
Docker: la plataforma de contenedores más popular, que permite empaquetar el software en unidades estandarizadas para su desarrollo, envío e implementación
Kata Containers: combina la velocidad de los contenedores con la seguridad de las máquinas virtuales, ofreciendo un entorno aislado para la ejecución de contenedores
containerd: un tiempo de ejecución estándar del sector centrado en la simplicidad, la solidez y la portabilidad, utilizado por Docker y Kubernetes
CRI-O: diseñado para Kubernetes, proporciona un tiempo de ejecución de contenedor ligero que cumple totalmente con la interfaz de ejecución de contenedores de Kubernetes
runc: una herramienta de CLI para generar y ejecutar contenedores de acuerdo con la especificación de la Open Container Initiative (OCI)
gVisor: un motor de ejecución de contenedores de código abierto, diseñado para proporcionar un entorno aislado para ejecutar contenedores, lo que mejora la seguridad al aislar la carga de trabajo del kernel del host
Administración y distribuciones de Kubernetes
Herramientas y plataformas diseñadas para simplificar la implementación, la administración y el funcionamiento de los clústeres de Kubernetes.
k3s: una distribución de Kubernetes ligera y fácil de instalar, ideal para entornos de computación periférica, IoT y CI/CD debido a sus requisitos mínimos de recursos
minikube: permite el funcionamiento de un clúster de Kubernetes en ordenadores personales, lo que resulta ideal para fines de desarrollo y pruebas
EKS (Amazon Elastic Kubernetes Service): un servicio gestionado que simplifica la ejecución de Kubernetes en AWS y en las instalaciones, proporcionando una integración perfecta con los servicios de AWS
Integración continua/implementación continua (CI/CD) y GitOps
Estas herramientas automatizan los pasos del proceso de entrega de software, como iniciar compilaciones, pruebas e implementaciones automáticas para agilizar el ciclo de vida del desarrollo.
Jenkins: Jenkins, un servidor de automatización de código abierto versátil, facilita la creación, las pruebas y la implementación del software, ya que admite una amplia gama de complementos para fines de CI/CD
Argo CD: se especializa en flujos de trabajo nativos de Kubernetes, lo que permite la entrega continua y automatiza los procesos de implementación directamente desde los repositorios de Git
Argo Workflows: una extensión de Argo como motor de flujo de trabajo para organizar trabajos paralelos en Kubernetes
Flux: adopta los principios de GitOps al aplicar automáticamente los cambios de Git a Kubernetes, lo que garantiza que el estado de los clústeres coincide con la configuración almacenada en el control de versiones. Flux aprovecha el kit de herramientas de GitOps para administrar los clústeres y las aplicaciones de Kubernetes. El kit de herramientas de GitOps proporciona un conjunto de API componibles y herramientas especializadas que permiten aplicar los principios de GitOps de forma continua, como la implementación de aplicaciones mediante cambios automatizados en los repositorios de Git.
________________


Seguridad y cumplimiento
Herramientas diseñadas para reforzar la seguridad y el cumplimiento en los entornos de Kubernetes, desde la implementación hasta el tiempo de ejecución.
Falco: detecta el comportamiento anormal de las aplicaciones y las posibles amenazas de seguridad en tiempo real mediante la supervisión de las llamadas al sistema y los registros de auditoría de Kubernetes
Kubescape: evalúa los clústeres de Kubernetes comparándolos con los estándares de seguridad conocidos y las mejores prácticas, e identifica los problemas de cumplimiento y las vulnerabilidades de acuerdo con las directrices de la NSA y la CISA.
OPA (Open Policy Agent): un motor de políticas versátil que hace cumplir las políticas en todos los ámbitos, garantizando el cumplimiento de las políticas y normativas de seguridad
Estructura de las 4C: En el contexto de la seguridad nativa de la nube, el orden correcto para la estructura de las 4C es:
 Nube: la seguridad comienza con la infraestructura de la nube, que proporciona las políticas y los controles de seguridad fundamentales.
 Clústeres: se centra en proteger los clústeres de Kubernetes o de orquestación de contenedores que ejecutan cargas de trabajo.
 Contenedores: implica proteger el tiempo de ejecución de los contenedores y garantizar que estén aislados y protegidos.
 Código: garantiza la seguridad del código de la aplicación, incluidas las prácticas de codificación seguras y la gestión de vulnerabilidades.
Contextos de seguridad: se definen a nivel de pod o contenedor y especifican la configuración de seguridad para los pods o contenedores individuales. Controlan aspectos como los privilegios de usuario, el acceso al sistema de archivos y las capacidades de un pod o contenedor específico. Los contextos de seguridad se centran en configurar la seguridad de los pods o contenedores individuales, especificando cómo deben ejecutarse.
Políticas de seguridad (PSP, Kyverno): funcionan a nivel de todo el clúster o del espacio de nombres y aplican los estándares de seguridad en varios pods, lo que garantiza que solo se puedan implementar los pods que cumplan con requisitos de seguridad específicos. Las políticas de seguridad se centran en hacer cumplir las reglas y políticas de seguridad para evitar que, en primer lugar, se programen o creen pods que no cumplan con los requisitos.




Almacenamiento en Kubernetes
Las soluciones de almacenamiento en Kubernetes son esenciales para la persistencia y la administración de los datos en entornos en contenedores, ya que permiten el aprovisionamiento y el escalado dinámicos.
Volúmenes: almacene datos para contenedores, lo que permite el almacenamiento efímero y persistente.
EmptyDir: almacenamiento temporal que se borra cuando se elimina un pod.
HostPath: monta un directorio desde el nodo host en un pod.
ConfigMap: proporciona datos de configuración para los pods. En Kubernetes, el ConfigMap puede utilizar el atributo immutable: true para garantizar que sus datos no se puedan modificar después de la creación. Esto es útil para optimizar el rendimiento y evitar actualizaciones accidentales.
Secreto: almacena datos confidenciales como contraseñas, tokens de API o claves SSH. En Kubernetes, las entidades secretas pueden utilizar el atributo inmutable: true para garantizar que sus datos no puedan modificarse después de su creación. Esto es útil para optimizar el rendimiento y evitar actualizaciones accidentales.


ETCD: fundamental para Kubernetes, ya que actúa como almacén principal del estado y los metadatos del clúster, lo que garantiza una alta disponibilidad y coherencia en un entorno distribuido
Rook: un orquestador de almacenamiento nativo de la nube de código abierto para Kubernetes, que proporciona la plataforma, el marco y el soporte para que un conjunto diverso de soluciones de almacenamiento se integren de forma nativa con los entornos nativos de la nube
Ceph: un sistema de almacenamiento distribuido y unificado diseñado para ofrecer un rendimiento, una fiabilidad y una escalabilidad excelentes
En Kubernetes, el almacenamiento efímero es un almacenamiento temporal vinculado al ciclo de vida de un pod. Se usa para datos no persistentes, como registros o archivos temporales, y se elimina cuando se cierra el pod.
En Kubernetes, el almacenamiento persistente se agrega a un pod mediante un PersistentVolume (PV) y un PersistentVolumeClaim (PVC). El PVC solicita almacenamiento y lo conectas al pod definiendo un volumen en el YAML del pod, que monta el almacenamiento en el contenedor. Este almacenamiento se mantiene mientras se reinicia el Pod.
Arquitecturas sin servidor y basadas en eventos
Estas herramientas ayudan a crear aplicaciones que pueden escalar de cero a escala planetaria sin administrar la infraestructura, centrándose en paradigmas basados en eventos y sin servidor.
KEDA (escalado automático basado en eventos de Kubernetes): escala dinámicamente las aplicaciones de Kubernetes en respuesta a eventos de diversas fuentes, lo que optimiza la utilización de los recursos
Knative: permite crear e implementar aplicaciones sin servidor y basadas en eventos en Kubernetes, lo que agiliza el desarrollo de aplicaciones nativas de la nube
________________


Administración de paquetes e implementación de aplicaciones
Simplificar la implementación y la administración de aplicaciones en Kubernetes con herramientas que administran paquetes y dependencias.
Helm: Helm, el gestor de paquetes de Kubernetes, agiliza el despliegue de aplicaciones mediante gráficos de Helm, que definen, instalan y actualizan incluso las aplicaciones de Kubernetes más complejas.
Mejores prácticas de Kubernetes
Uso del espacio de nombres: utilice los espacios de nombres para separar de forma lógica los recursos y las políticas de los diferentes entornos (por ejemplo, desarrollo, prueba o producción).
Solicitudes y límites de recursos: define las solicitudes y los límites de CPU y memoria para garantizar que los pods obtengan los recursos que necesitan sin sobreaprovisionar.
Uso de etiquetas y selectores: usa etiquetas para organizar y seleccionar grupos de objetos en Kubernetes.
Administración de la configuración: almacene la configuración por separado del código de la aplicación mediante ConfigMaps y Secrets.
Seguridad en Kubernetes
Control de acceso basado en funciones (RBAC): controla el acceso a la API de Kubernetes en función de las funciones y los permisos.
Políticas de seguridad de los pods (PSP): controlan el contexto de seguridad en el que funcionan los pods, incluidos los privilegios y el acceso al sistema de archivos. Los contextos de seguridad de Kubernetes se asocian principalmente a la definición de la configuración de seguridad de los pods o los contenedores. Estas configuraciones controlan aspectos como los privilegios de los usuarios, los permisos del sistema de archivos y las capacidades, y garantizan que los contenedores funcionen con el nivel de seguridad adecuado.
Políticas de red: defina qué pods pueden comunicarse entre sí y con terminales externos. En Kubernetes, las políticas de red son aditivas. Cuando varias políticas se dirigen a los mismos módulos, solo se permite el tráfico permitido por todas las políticas, lo que genera reglas cada vez más restrictivas.
Administración de secretos: usa Kubernetes Secrets para almacenar datos confidenciales, pero considera la posibilidad de usar herramientas externas como HashiCorp Vault para tus necesidades de seguridad avanzadas.
Seguridad de la imagen: asegúrese de que los contenedores se construyan a partir de fuentes confiables y se escaneen para detectar vulnerabilidades (por ejemplo, con herramientas como Clair o Trivy).
Los contextos de seguridad de Kubernetes se asocian principalmente a la definición de la configuración de seguridad de los pods o contenedores. Estas configuraciones controlan aspectos como los privilegios de los usuarios, los permisos del sistema de archivos y las capacidades, y garantizan que los contenedores funcionen con el nivel de seguridad adecuado.
Solución de problemas de Kubernetes
Comandos de kubectl:
kubectl get: muestra los recursos, como los pods, las implementaciones y los servicios.
kubectl describe: proporciona información detallada sobre un recurso.
kubectl logs: obtiene los registros de un contenedor en ejecución.
kubectl exec: ejecuta un comando dentro de un contenedor.
kubectl top: muestra el uso de recursos de los nodos y pods.
Errores comunes:
ImagePullbackoff: Kubernetes no puede extraer la imagen del contenedor especificada. Esto suele ocurrir debido a un nombre de imagen incorrecto, a que falta una imagen en el registro o a problemas de autenticación con un registro privado.
CrashLoopBackoff: el contenedor del pod no se inicia repetidamente. Esto puede deberse a bloqueos de la aplicación, a una configuración incorrecta o a la falta de dependencias.
ErrimagePull: Kubernetes no pudo extraer la imagen del contenedor del registro. Por lo general, esto se debe a un nombre de imagen incorrecto, a que la imagen no existe o a un problema de red.
ImageInspectError: Kubernetes no puede inspeccionar la imagen después de extraerla, a menudo debido a problemas de corrupción o compatibilidad.
ErriImageNeverPull: la ImagePullPolicy está configurada como «Nunca», pero la imagen no está presente en el nodo. Kubernetes está configurado para no extraer la imagen, pero no puede encontrarla localmente.
CreateContainerConfigError: Kubernetes no puede crear la configuración del contenedor. Esto puede deberse a una configuración no válida, como variables de entorno incorrectas, montajes de volumen o falta de secretos.
CreateContainerError: el contenedor no se puede crear, a menudo debido a problemas con la configuración subyacente de Docker o a que falta una imagen.
invalidImageName: el nombre de la imagen del contenedor especificado en la especificación del pod no es válido. Esto puede deberse a errores tipográficos o a un formato incorrecto.
Conflictos de afinidad o antiafinidad entre nodos o pods: la programación del pod falla debido a conflictos en las reglas de afinidad o antiafinidad de los nodos o los pods. Esto evita que el pod se programe en cualquier nodo disponible.
NodeNotReady: el nodo en el que está programado el pod no está listo, posiblemente debido a un problema con la configuración o la conectividad del nodo.
Pendiente: el pod está atascado en estado pendiente, a menudo porque no hay suficientes recursos (CPU, memoria) en los nodos o porque ningún nodo cumple con los requisitos de programación del pod.
containerCanNotRun: el contenedor se inicia pero falla inmediatamente. Esto puede deberse a un comando o punto de entrada no válido, a variables de entorno incorrectas o a la falta de dependencias en el contenedor.
oomKilled: el eliminador de la falta de memoria (OOM) de Kubernetes canceló el contenedor porque superaba sus límites de memoria.
Fecha límite superada: la tarea o el pod no se completaron en el límite de tiempo especificado. Esto suele ocurrir con Kubernetes Jobs o CronJobs que tienen un límite de tiempo.
Desalojado: el pod se desalojó del nodo debido a limitaciones de recursos, como la presión del disco, la presión de la memoria o los límites de la CPU.
No se puede programar: el pod no se puede programar en ningún nodo. Esto suele ocurrir debido a la falta de recursos, a problemas con la selección de nodos o a problemas con la selección de nodos.
DNSResolutionError: el pod no puede resolver los nombres de DNS, a menudo debido a problemas con el servicio DNS de Kubernetes o con las políticas de red que bloquean el tráfico de DNS.
VolumeMountError: Kubernetes no puede montar el volumen especificado en la especificación del pod, a menudo debido a una configuración incorrecta, a la falta de PersistentVolumeClaims (PVC) o a problemas de permisos.
VolumeNotFound: no se puede encontrar el volumen especificado en la configuración del pod, a menudo porque falta un PersistentVolume (PV) o PersistentVolumeClaim (PVC).
Fallo en la sonda de disponibilidad o disponibilidad: el pod no pasa las sondas de disponibilidad o disponibilidad, lo que hace que Kubernetes lo marque como no listo o lo reinicie.
No autorizado: Kubernetes no puede autenticarse en el servidor API ni en un registro de contenedores privado porque las credenciales no son válidas o los tokens han caducado.
Prohibido: una acción está bloqueada debido a la falta de permisos, a menudo relacionados con las políticas de control de acceso basado en roles (RBAC).
ConfigMapKeyreError: Kubernetes no puede encontrar una clave específica en el ConfigMap al que hace referencia el pod o la implementación, lo que provoca un error cuando el pod intenta iniciarse.
SecretKeyreError: al igual que «ConfigMapKeyreError», esto ocurre cuando Kubernetes no puede encontrar una clave específica en el secreto al que hace referencia el pod.
ServiceUnavailable: el servicio Kubernetes no está disponible, a menudo debido a problemas con los pods de servicio o la red subyacentes.
Pod CrashLoopBackoff: el pod se bloquea repetidamente; investiga los registros con los registros de kubectl.
Pods pendientes: los pods no se pueden programar, a menudo debido a la falta de recursos o a reglas de afinidad.
Comandos comunes e importantes de Kubernetes
Comandos básicos
versión kubectl
Muestra la versión de Kubernetes del cliente y del servidor.
 Ejemplo:
versión kubectl
kubectl get [recurso]
Muestra uno o más recursos de un tipo específico, como pods, despliegues o servicios.
Ejemplo:
kubectl obtiene cápsulas
kubectl obtiene servicios
kubectl obtiene despliegues
kubectl describe [recurso] [nombre]
Muestra información detallada sobre un recurso específico.
 Ejemplo:
kubectl describe el pod [nombre del pod]
kubectl describe el servicio [nombre-servicio]
kubectl registra [nombre del pod]
Obtiene los registros de un pod. Añade -f para seguir los registros en tiempo real.
Ejemplo:
kubectl registra [nombre del pod]
kubectl registra -f [nombre del pod]
El comando kubectl logs con el indicador --previous se usa para ver los registros de un contenedor terminado en un pod con varios contenedores en Kubernetes.
Ejemplo:
<pod-name><container-name>kubectl registra -c --previous
La marca --previous se puede abreviar como --p
kubectl exec [nombre del pod] -- [comando]
Ejecuta un comando dentro de un contenedor en ejecución de un pod.
 Ejemplo:
kubectl exec [nombre del pod] -- [comando]
kubectl exec -it [nombre del pod] -- /bin/sh
kubectl elimina [recurso] [nombre]
Elimina un recurso específico.
Ejemplo:
kubectl delete pod [nombre del pod]
kubectl elimina la implementación [nombre de la implementación]
recursos de la API de kubectl
El comando kubectl se usa para enumerar todos los recursos de API, como los pods, los servicios y las implementaciones, disponibles en un clúster de Kubernetes. Este comando muestra una lista de todos los recursos disponibles, junto con sus nombres abreviados, el grupo de API y si tienen un espacio de nombres o no.
Creación y exposición de recursos
kubectl create -f [file.yaml]
Crea un recurso mediante un archivo de configuración YAML o JSON.
 Ejemplo:
kubectl create -f [archivo.yaml]
kubectl expose [recurso] --port= [puerto] --target-port= [puerto-objetivo]
Expone un recurso, como un pod o una implementación, como un servicio.
Ejemplo:
kubectl expose pod [nombre del pod] --port=80 --target-port=8080
kubectl expose deployment [nombre-despliegue] --type=nodeport --port=80
kubectl apply -f [file.yaml]
Aplica una configuración a un recurso por nombre de archivo o stdin.
 Ejemplo:
kubectl apply -f [archivo.yaml]
kubectl scale [recurso] --replicas= [num]
Amplía una implementación o un ReplicaSet al número deseado de réplicas.
Ejemplo:
implementación a escala de kubectl [nombre de la implementación] --replicas=5
Visualización del estado de los recursos
kubectl obtiene cápsulas de -o de ancho
Muestra todos los pods con detalles adicionales, como el estado del nodo, la IP y el contenedor.
 Ejemplo:
kubectl obtiene vainas de -o de ancho
kubectl: nodos/cápsulas superiores
Muestra el uso de recursos (CPU/memoria) de los nodos o pods.
Ejemplo:
nodos principales de kubectl
Los mejores pods de kubectl
kubectl recibe eventos
Muestra los eventos recientes del clúster.
 Ejemplo:
kubectl obtiene eventos
________________


Administración del espacio de nombres
kubectl obtiene los espacios de nombres
Muestra todos los espacios de nombres del clúster.
Ejemplo:
kubectl obtiene los espacios de nombres
kubectl crea un espacio de nombres [espacio de nombres]
Crea un nuevo espacio de nombres.
 Ejemplo:
kubectl crea un espacio de nombres [espacio de nombres]
kubectl elimina el espacio de nombres [espacio de nombres]
Elimina un espacio de nombres y todos los recursos que contiene.
Ejemplo:
kubectl elimina el espacio de nombres [espacio de nombres]
kubectl config set-context --current --namespace= [espacio de nombres]
Cambia el contexto actual al espacio de nombres especificado.
 Ejemplo:
kubectl config set-context --current --namespace= [espacio de nombres]
Recursos de edición y aplicación de parches
kubectl edit [recurso] [nombre]
Abre un editor para modificar la configuración de un recurso.
Ejemplo:
kubectl edit pod [nombre del pod]
kubectl patch [recurso] [nombre] --patch [json|yaml]
Actualiza un recurso mediante un parche.
 Ejemplo:
kubectl patch deployment [nombre-despliegue] --patch '{"spec»: {"replicas» :3}}'
________________


Depuración y solución de problemas
kubectl describe [recurso] [nombre]
Proporciona información detallada sobre un recurso, incluidos los eventos recientes y los cambios de estado.
Ejemplo:
kubectl describe el pod [nombre del pod]
kubectl get pod [nombre del pod] -o yaml
Genera la configuración completa de YAML de un recurso.
 Ejemplo:
kubectl get pod [nombre del pod] -o yaml
kubectl port-forward [nombre del pod] [puerto local]: [puerto remoto]
Reenvía un puerto local a un puerto de un pod para su depuración.
Ejemplo:
kubectl port-forward pod/ [nombre del pod] 8080:80
Gestión de trabajos y CronJob
kubectl crea un trabajo [nombre del trabajo] --image= [imagen]
Crea un trabajo que ejecuta una imagen específica.
 Ejemplo:
kubectl crea trabajo [nombre del trabajo] --image=busybox
kubectl consigue trabajos
Muestra todos los trabajos.
Ejemplo:
kubectl consigue trabajos
kubectl crea cronjob [nombre] --image= [image] --schedule= "[cron-schedule]»
Crea un CronJob que se ejecuta de forma programada.
 Ejemplo:
kubectl crea cronjob [cronjob-name] --image=busybox --schedule="/5»
________________


Control de acceso basado en roles y cuentas de servicio (RBAC)
kubectl crea una cuenta de servicio [nombre de la cuenta]
Crea una nueva cuenta de servicio.
Ejemplo:
kubectl crea una cuenta de servicio [nombre de la cuenta]
kubectl obtiene cuentas de servicio
Muestra todas las cuentas de servicio.
 Ejemplo:
kubectl obtiene cuentas de servicio
kubectl create rolebinding [binding-name] --clusterrole= [role] --serviceaccount= [namespace]: [account] --namespace= [namespace]
Vincula un rol a una cuenta de servicio en un espacio de nombres específico.
Ejemplo:
kubectl create rolebinding [binding-name] --clusterrole=view --serviceaccount=default: [nombre de cuenta] --namespace=default
Gestión del contexto y la configuración
vista de configuración de kubectl
Muestra la configuración actual del contexto de Kubernetes.
 Ejemplo:
vista de configuración de kubectl
kubectl config get-contexts
Muestra todos los contextos disponibles.
Ejemplo:
kubectl config get-contexts
kubectl config use-context [nombre-contexto]
Cambia a un contexto de Kubernetes diferente.
 Ejemplo:
kubectl config use-context [nombre-contexto]
________________


Certificados y seguridad
Certificados TLS en Kubernetes
El TLS (Transport Layer Security) garantiza una comunicación segura entre los componentes de Kubernetes, como el servidor API, Kubelet, etc.
Los componentes de Kubernetes se comunican a través de un HTTPS seguro mediante certificados TLS.
Los certificados TLS normalmente se generan automáticamente cuando se usa kubeadm o se pueden administrar manualmente.
Componentes clave que utilizan certificados TLS:
 kube-apiserver: el servidor de API debe tener un certificado para proteger sus comunicaciones.
 etcd: asegura la comunicación entre los miembros y los clientes de etcd (como el kube-apiserver).
 kubelet: cada kubelet tiene un certificado de cliente para autenticarse en el kube-apiserver.
 Rotación de certificados:
 Kubernetes gestiona automáticamente la rotación de los certificados mediante kube-controller-manager. Los administradores deben asegurarse de que la caducidad del certificado no afecte al clúster.
Comando para comprobar la caducidad de los certificados de Kubernetes:
sudo openssl x509 -noout -enddate -in /etc/kubernetes/pki/apiserver.crt
Solicitudes de firma de certificados (CSR)
 Kubernetes puede gestionar las solicitudes de firma de certificados (CSR), en las que un kubelet u otro componente solicita un certificado al clúster.
Los administradores pueden aprobar, denegar o firmar manualmente las CSR mediante el comando kubectl certificate.
Ejemplos de comandos:
kubectl get csr
certificado kubectl aprobado <csr-name>
________________
KubeConfig
 KubeConfig es el archivo de configuración que define cómo conectarse a los clústeres de Kubernetes.
 Almacena información como clústeres, usuarios y contextos para interactuar con varios clústeres.
Campos clave del archivo ~/.kube/config:
clústeres: define las direcciones y los certificados de los clústeres.
usuarios: almacena información de autenticación, como tokens o certificados.
contextos: asocia usuarios con clústeres.
Contextos de conmutación:
contexto de uso de configuración de kubectl <context-name>
Asegurar el servidor API
El servidor de API es el principal punto de entrada al clúster y necesita los controles de seguridad adecuados.
El modo --authorization-mode predeterminado en el servidor de API de Kubernetes es Node, RBAC y AlwaysAllow, lo que permite permisos a nivel de nodo, control de acceso basado en roles y acceso sin restricciones si no se aplica ninguna otra política.
Medidas de seguridad clave:
Control de acceso basado en roles (RBAC): controla quién puede acceder a qué recursos del clúster.
Controladores de admisión: módulos que rigen el comportamiento de las solicitudes. Importantes:
Restricción de nodos: evita que los nodos modifiquen los recursos de otros nodos.
PodSecurityPolicies (en desuso): regula la configuración de seguridad a nivel de pod.
Utilice Open Policy Agent (OPA) o Kyverno como sustitutos de los PSP.
________________


Adiciones de redes
CNI (interfaz de red de contenedores)
Los complementos del CNI administran las configuraciones de red y la conectividad entre los pods de un clúster de Kubernetes.
Kubernetes admite varios complementos de CNI, cada uno de los cuales ofrece funciones únicas:
Calico: proporciona políticas de red y redes con enrutamiento opcional basado en BGP.
Flannel: un proveedor de redes superpuestas simple que asigna subredes a los nodos.
Weave Net: una solución de red basada en mallas.
Cilium: utiliza eBPF para proporcionar redes, seguridad y observabilidad avanzadas.
Instalación de complementos de CNI:
El complemento CNI debe estar instalado en cada nodo para permitir la comunicación con el pod.
 <plugin.yaml> Los manifiestos del plugin CNI se pueden aplicar mediante kubectl apply -f.
Configuración de CoreDNS
CoreDNS es el servicio de DNS de Kubernetes que proporciona resolución interna de nombres para servicios y pods.
La configuración de CoreDNS implica actualizar el ConfigMap de CoreDNS, que normalmente se encuentra en el espacio de nombres del sistema kube.
Ejemplo:
kubectl edit configmap coredns -n kube-system
Problemas comunes de CoreDNS:
Pueden producirse problemas de resolución de nombres de DNS si CoreDNS no funciona o está mal configurado.
Depuración de DNS:
kubectl get pods -n kube-system -l k8s-app=kube-dns
kubectl registra <coredns-pod>-n kube-system


________________
Políticas de red
Las políticas de red definen la forma en que los pods se comunican entre sí y con los sistemas externos. En Kubernetes, las políticas de red son aditivas. Cuando se aplican varias políticas a los mismos pods, solo se permite el tráfico permitido por todas las políticas. Cada política añade restricciones, por lo que el resultado es más restrictivo a medida que se aplican más políticas.
Ejemplo de una política de red que solo permite el tráfico a un pod desde pods del mismo espacio de nombres:
Versión de API: networking.k8s.io/v1
tipo: NetworkPolicy
metadatos:
nombre: allow-same-namespace
espacio de nombres: predeterminado
especificación:
PodSelector: {}
Tipos de políticas:
- Entrada
Entrada:
- desde:
- PodSelector: {}
Programación avanzada
Afinidad y antiafinidad de los pods
La afinidad de los pods garantiza que los pods estén programados en nodos cercanos a otros pods específicos.
La antiafinidad de los pods garantiza que los pods se programen en lugar de otros pods específicos.
Ejemplo de PodAffinity:
afinidad:
Afinidad de pod:
Necesario durante la programación, ignorado durante la ejecución:
- Selector de etiquetas:
Expresiones coincidentes:
- clave: aplicación
operador: En
valores:
- interfaz
Clave de topología: «kubernetes.io/nombre de host»
Afinidad de nodos y condiciones/tolerancias
La afinidad de nodos garantiza que los pods se programen en los nodos que coinciden con determinadas etiquetas.
Ejemplo de afinidad de nodos:
afinidad:
Afinidad de nodo:
Necesario durante la programación, ignorado durante la ejecución:
Términos del selector de nodos:
- Expresiones coincidentes:
- clave: «kubernetes.io/e2e-az-name»
operador: En
valores: ["e2e-az1", «e2e-az2"]
Contaminaciones: se utilizan para hacer que un nodo «no esté disponible», a menos que el pod tenga una tolerancia coincidente.
Contaminar un nodo:
kubectl: nodos contaminados: node1: key=value:noschedule
Actualizaciones de Kubernetes
Política de sesgo de versiones
Kubernetes admite el sesgo de versiones, donde kubelet puede estar una versión secundaria por detrás del plano de control.
 Asegúrese de actualizar primero los componentes del plano de control y, a continuación, los nodos de trabajo.
Actualización de un clúster de Kubernetes
Actualización de un clúster administrado por kubeadm:
plan de actualización de kubeadm
solicitar la actualización de kubeadm <version>
Actualice kubelet y kubectl después de actualizar el plano de control:
sudo apt-get update && sudo apt-get install -y kubelet kubectl
________________


Clústeres de alta disponibilidad (HA)
Configuración del plano de control HA de Kubernetes
 Un plano de control de alta disponibilidad incluye varios servidores de API, instancias, etc. y un balanceador de cargas.
 Debes configurar un balanceador de cargas para distribuir el tráfico entre los servidores de API.
Copia de seguridad y restauración de Etcd
Haga una copia de seguridad de etcd usando etcdctl:
etcdctl snapshot save /path/to/backup.db
Restaurar etcd:
etcdctl: snapshot restore: /path/to/backup.db


Recuperación ante desastres
Estrategias de recuperación ante desastres
 Mantenga siempre instantáneas de etcd.
 Mantenga copias de seguridad de los manifiestos del clúster y utilice GitOps para conocer el estado de la infraestructura.
Operadores de Helm y Kubernetes
Conceptos básicos de Helm Templating
 Helm es el administrador de paquetes de Kubernetes. Los gráficos de Helm definen, instalan y actualizan los recursos de Kubernetes.
Ejemplo de una estructura de gráficos de Helm:
mychart/
Chart.yaml # Metadatos sobre el gráfico
values.yaml # Valores predeterminados para las plantillas
templates/ # Los recursos de Kubernetes se definen aquí


Operadores de Kubernetes
Los operadores amplían la funcionalidad de Kubernetes al automatizar el ciclo de vida de las aplicaciones mediante controladores personalizados.
________________
Espacios de nombres
Los espacios de nombres proporcionan una forma de dividir los recursos del clúster entre varios usuarios o equipos. Ayudan a organizar y gestionar los objetos de Kubernetes, como los pods, los servicios y las implementaciones, de forma lógica.
 Puntos clave:
 De forma predeterminada, Kubernetes viene con cuatro espacios de nombres:
 predeterminado: el espacio de nombres predeterminado para los objetos sin ningún otro espacio de nombres especificado.
kube-system: contiene los componentes del sistema Kubernetes (por ejemplo, kube-dns).
kube-public: de acceso público, normalmente se usa para recursos que deberían estar visibles en todo el clúster.
 kube-node-lease: se usa para los latidos del corazón de los nodos.
Comandos de espacio de nombres:
# Listar todos los espacios de nombres
kubectl obtiene los espacios de nombres


# Crea un nuevo espacio de nombres
kubectl crea un espacio de nombres <namespace-name>


# Eliminar un espacio de nombres
kubectl elimina un espacio de nombres <namespace-name>


# Cambie a un espacio de nombres específico
kubectl config set-context --current --namespace= <namespace-name>
________________
Objetos
Los objetos de Kubernetes son entidades persistentes en el sistema Kubernetes. Representan el estado deseado del clúster (p. ej., aplicaciones en ejecución, configuraciones de carga de trabajo).
Objetos comunes:
Pod: la unidad desplegable más pequeña, que representa uno o más contenedores.
Servicio: expone una aplicación como un servicio de red.
 Implementación: administra las aplicaciones sin estado y gestiona las actualizaciones y el escalado.
ReplicaSet: garantiza que se esté ejecutando una cantidad específica de pods idénticos en un momento dado.
StatefulSet: administra las aplicaciones con estado.
 Trabajo: administra los trabajos por lotes, garantizando que los pods se ejecuten hasta su finalización.
ConfigMap: contiene los datos de configuración como pares clave-valor.
 Secreto: contiene datos confidenciales como contraseñas o claves de API.
API de Kubernetes
 La API de Kubernetes es la interfaz de administración central para interactuar con los componentes de Kubernetes. Expone todas las operaciones del clúster a través de puntos finales RESTful.
 El servidor API es la interfaz del plano de control, que procesa las solicitudes de API REST.
 Recursos de API comunes:
 /api/v1: accede a los recursos principales de Kubernetes (pods, servicios, nodos, etc.).
/apis/apps/v1: accede a recursos adicionales (despliegues, conjuntos de estado, etc.).
Ejemplo de llamada a la API con curl:
<api-server>curl https:///api/v1/namespaces/default/pods
 Tanto kubectl como los componentes internos utilizan la API de Kubernetes para interactuar con el clúster.
________________
Control de acceso basado en roles (RBAC)
El RBAC es un mecanismo de Kubernetes para controlar quién puede acceder a qué recursos del clúster.
 Componentes clave:
 Función: otorga permisos dentro de un espacio de nombres específico.
 ClusterRole: otorga permisos en todo el clúster.
 RoleBinding: asocia un rol con usuarios o cuentas de servicio dentro de un espacio de nombres.
 ClusterRoleBinding: asocia un ClusterRole a los usuarios de todo el clúster.
Ejemplo: creación de un rol y un enlace de roles:
Versión de API: rbac.authorization.k8s.io/v1
tipo: Rol
metadatos:
espacio de nombres: predeterminado
nombre: pod-reader
reglas:
- Grupos de API: [""]
recursos: ["pods"]
verbos: ["obtener», «ver», «listar"]
---
Versión de API: rbac.authorization.k8s.io/v1
tipo: RoleBinding
metadatos:
nombre: read-pods
espacio de nombres: predeterminado
temas:
- tipo: Usuario
nombre: «jane»
Grupo API: rbac.authorization.k8s.io
Ref de rol:
tipo: Rol
nombre: pod-reader
Grupo API: rbac.authorization.k8s.io
________________
Cápsulas
 Un pod es la unidad desplegable más pequeña de Kubernetes y representa una única instancia de una aplicación que se ejecuta en un contenedor.
 Conceptos clave:
 Un pod puede ejecutar uno o más contenedores, que están estrechamente acoplados y comparten la misma red y almacenamiento.
 Los pods son efímeros por naturaleza, lo que significa que se crean y destruyen de forma dinámica.
Ejemplo de configuración de un pod:
Versión de API: v1
tipo: Pod
metadatos:
nombre: nginx
etiquetas:
aplicación: nginx
especificación:
contenedores:
- nombre: nginx
imagen: nginx
puertos:
- Puerto de contenedores: 80
________________
Implementaciones
 Una implementación es un objeto de Kubernetes de nivel superior que se utiliza para administrar aplicaciones sin estado. Define el estado deseado de la aplicación (por ejemplo, cuántas réplicas de un pod deben estar ejecutándose).
 Características principales:
 Actualizaciones continuas: garantiza que no haya ningún tiempo de inactividad al actualizar las aplicaciones. Las implementaciones de Kubernetes utilizan la estrategia RollingUpdate de forma predeterminada, que reemplaza gradualmente los pods antiguos por otros nuevos para minimizar el tiempo de inactividad. Controla el proceso de actualización mediante maxSurge (se permiten pods adicionales) y maxUnavailable (pods que pueden no estar disponibles).
 Escalado: puedes escalar los pods hacia arriba o hacia abajo ajustando el número de réplicas.
 Autocuración: reemplaza automáticamente a las cápsulas enfermas.
Ejemplo de configuración de despliegue:
Versión de API: apps/v1
tipo: Despliegue
metadatos:
nombre: nginx-deployment
especificación:
réplicas: 3
selector:
Etiquetas coincidentes:
aplicación: nginx
plantilla:
metadatos:
etiquetas:
aplicación: nginx
especificación:
contenedores:
- nombre: nginx
imagen: nginx:1.14.2
puertos:
- Puerto de contenedores: 80
________________
Conjuntos de réplicas
 Un ReplicaSet garantiza que se esté ejecutando un número específico de réplicas de pods en todo momento.
 Características principales:
 Garantiza que se esté ejecutando la cantidad deseada de pods añadiendo o quitando pods según sea necesario.
 Las implementaciones usan ReplicaSets internamente para mantener las réplicas de los pods.
Ejemplo de configuración de ReplicaSet:
Versión de API: apps/v1
tipo: ReplicaSet
metadatos:
nombre: nginx-replicaset
especificación:
réplicas: 3
selector:
Etiquetas coincidentes:
aplicación: nginx
plantilla:
metadatos:
etiquetas:
aplicación: nginx
especificación:
contenedores:
- nombre: nginx
imagen: nginx
________________
Entrada
 Ingress es un objeto de API que administra el acceso externo a los servicios dentro de un clúster de Kubernetes, normalmente rutas HTTP/HTTPS.
 Características principales:
 Puede definir reglas para enrutar el tráfico externo a los servicios internos.
 Soporta la terminación SSL/TLS para comunicaciones seguras.
Ejemplo de configuración de ingreso:
Versión de API: networking.k8s.io/v1
tipo: Ingress
metadatos:
nombre: example-ingress
anotaciones:
nginx.ingress.kubernetes.io/rewrite-target:/
especificación:
reglas:
- anfitrión: example.com
http:
rutas:
- ruta:/
Tipo de ruta: Prefijo
backend:
servicio:
nombre: my-service
puerto:
número: 80
________________
Escalado automático vertical
 El escalado automático vertical ajusta de forma dinámica las solicitudes de recursos y los límites de los pods en función de su uso.
 Esto es útil para aplicaciones que necesitan más CPU o memoria bajo carga, pero no requieren escalarse en términos del número de réplicas.
 Características principales:
 El escalador automático Vertical Pod (VPA) ajusta automáticamente la CPU y la memoria de los pods.
 Ayuda a mejorar la utilización de los recursos y evita el sobreaprovisionamiento.
Escalado automático de clústeres
 El escalador automático de clústeres ajusta automáticamente la cantidad de nodos de un clúster en función de las demandas de recursos de las cargas de trabajo.
 Características principales:
 Añade nodos cuando los pods no se pueden programar por falta de recursos.
 Elimina los nodos infrautilizados cuando disminuyen las cargas de trabajo.
 Activación del escalador automático de clústeres:
 La mayoría de los servicios gestionados de Kubernetes (por ejemplo, AWS EKS, GCP GKE o Azure AKS) incluyen el escalador automático de clústeres como una función integrada.
 Requiere definir los recuentos mínimos y máximos de nodos para el clúster.
CI/CD
 La CI/CD (integración continua/entrega continua) se refiere al proceso de crear, probar e implementar automáticamente los cambios de código en un entorno de producción.
 Conceptos clave:
 Integración continua (CI): los desarrolladores combinan con frecuencia los cambios de código en un repositorio compartido y realizan pruebas automatizadas para garantizar la calidad.
 Entrega continua (CD): automatiza la implementación de los cambios de código en los entornos de producción o ensayo.
 Herramientas comunes:
 Jenkins: un servidor de automatización de código abierto que permite crear, probar e implementar código.
 Argo CD: una herramienta de entrega continua nativa de Kubernetes que sigue el modelo de GitOps.
 Flux: otra solución de entrega continua nativa de Kubernetes.
________________
Metodología de 12 factores para crear aplicaciones nativas de la nube
La metodología de aplicaciones de 12 factores es un conjunto de mejores prácticas para crear aplicaciones nativas de la nube modernas, escalables y fáciles de mantener.
1. Base de código: se rastrea una base de código en el control de versiones, muchas implementaciones.
2. Dependencias: declare y aísle explícitamente las dependencias.
3. Configuración: Almacene la configuración en el entorno.
4. Servicios de respaldo: trate los servicios de respaldo (como las bases de datos) como recursos adjuntos.
5. Construir, lanzar y ejecutar: separe estrictamente las etapas de compilación y ejecución.
6. Procesos: ejecuta la aplicación como uno o más procesos sin estado.
7. Vinculación de puertos: servicios de exportación mediante enlace de puertos
8. Concurrencia: escale mediante el modelo de proceso.
 Las aplicaciones deben diseñarse para gestionar el escalamiento de la carga de trabajo mediante la ejecución de varios procesos (instancias) en contenedores o máquinas virtuales. Kubernetes se destaca en la gestión de este proceso a través de Pods y ReplicaSets.
8. Desechabilidad: maximice la robustez con un arranque rápido y un apagado sin problemas.
 Las aplicaciones deben diseñarse para que se inicien rápidamente y se cierren correctamente. Kubernetes ayuda en este sentido mediante sondeos de preparación y funcionamiento para gestionar el ciclo de vida de los contenedores.
9. Paridad entre desarrollo y producción: mantenga el desarrollo, la puesta en escena y la producción lo más similares posible.
 Al usar entornos en contenedores y herramientas de orquestación como Kubernetes, los equipos pueden mantener la paridad entre los entornos de desarrollo, preparación y producción, minimizando así los problemas de «todo funciona en mi máquina».
11. Registros: trate los registros como transmisiones de eventos.
 Las aplicaciones no deben administrar ni almacenar sus propios archivos de registro. En su lugar, los registros deben enviarse a stdout/stderr, donde pueden capturarse y agregarse mediante sistemas de registro centralizados como Fluentd, ELK (Elasticsearch, Logstash, Kibana) o Prometheus/Grafana.
12. Procesos de administración: ejecute las tareas de administración y gestión como procesos únicos.
 Las tareas administrativas, como las migraciones de bases de datos, las copias de seguridad y la limpieza de datos, deben tratarse como tareas puntuales y efímeras, que a menudo se gestionan mediante Kubernetes Jobs o CronJobs.
________________
Conceptos adicionales a tener en cuenta:
Service Mesh (más allá de las aplicaciones de 12 factores)
 Una malla de servicios brinda soporte a nivel de infraestructura para administrar las comunicaciones de servicio a servicio dentro de una arquitectura de microservicios nativa de la nube.
 Herramientas populares:
 Istio: proporciona administración del tráfico, observabilidad, seguridad y aplicación de políticas.
 Linkerd: una red de servicios ligera y de alto rendimiento centrada en la simplicidad y la seguridad.
 Consul: una herramienta de red de servicios para el descubrimiento de servicios, la verificación del estado y el control del tráfico.
 Principales beneficios de una malla de servicios:
 Observabilidad: proporciona métricas, registros y rastreo de los servicios.
 Control del tráfico: puede aplicar reglas para el enrutamiento del tráfico, el equilibrio de carga y los reintentos.
 Seguridad: aplica el TLS mutuo (mTLS) entre los servicios, lo que garantiza una comunicación segura.
Observabilidad nativa de la nube
 La observabilidad se refiere a la capacidad de medir los estados internos de un sistema mediante el examen de sus resultados (métricas, registros, trazas).
Herramientas clave:
Prometheus: una herramienta de monitoreo que recopila datos de series temporales y los expone a través de una API para generar alertas o visualizaciones.
Grafana: funciona con Prometheus para crear paneles y visualizar las métricas recopiladas.
Jaeger: una herramienta de rastreo distribuido para rastrear el flujo de solicitudes en arquitecturas de microservicios.
Componentes de observabilidad en Kubernetes:
Registros: se pueden recopilar mediante herramientas como Fluentd o Elastic Stack.
Métricas: herramientas como Prometheus y Kubernetes Metrics Server recopilan métricas para escalarlas y supervisarlas automáticamente.
Rastreo: las herramientas de rastreo distribuidas, como Jaeger o Zipkin, proporcionan información sobre las comunicaciones entre servicios.
________________
GitOps para Kubernetes
GitOps es un conjunto de prácticas que utilizan Git como la única fuente confiable para administrar los clústeres de Kubernetes.
Herramientas clave:
1. Argo CD: una herramienta de entrega continua diseñada específicamente para Kubernetes que sigue la metodología GitOps.
2. Flux: otra herramienta de GitOps que automatiza las implementaciones en función de los cambios introducidos en un repositorio de Git.
 Flujo de trabajo de GitOps:
1. Defina el estado deseado de los recursos de Kubernetes en un repositorio de Git.
2. Cuando se realizan cambios en el repositorio de Git (como configuraciones actualizadas o nuevas implementaciones), herramientas como Argo CD o Flux aplican automáticamente los cambios al clúster de Kubernetes.
3. Estas herramientas comparan continuamente el estado real del clúster con el estado deseado definido en Git y toman medidas correctivas si es necesario.
Los microservicios frente a las aplicaciones monolíticas en el desarrollo nativo de la nube
 Arquitectura de microservicios: divide las aplicaciones en servicios pequeños, poco acoplados e implementables de forma independiente que se comunican a través de API.
Ventajas de los microservicios:
Escalabilidad: cada servicio se puede escalar de forma independiente.
Resiliencia: las fallas en un servicio no necesariamente afectan a todo el sistema.
Implementación más rápida: cada servicio se puede desarrollar, probar e implementar de forma independiente, lo que permite ciclos de lanzamiento más rápidos.
Arquitectura monolítica: una aplicación única y grande en la que todos los componentes están estrechamente integrados.
Desafíos de la arquitectura monolítica:
 Escalabilidad: requiere escalar toda la aplicación, incluso si solo una parte necesita más recursos.
 Complejidad de la implementación: los pequeños cambios pueden requerir la reimplementación de toda la aplicación.
 Mantenimiento: se hace cada vez más difícil de mantener y probar a medida que la aplicación crece.
 Kubernetes y microservicios: Kubernetes es ideal para la arquitectura de microservicios, ya que admite el escalado dinámico, el descubrimiento de servicios y la gestión del tráfico.
________________
Sin servidor en Kubernetes
 La computación sin servidor permite a los desarrolladores crear y ejecutar aplicaciones sin administrar la infraestructura. En Kubernetes, herramientas como Knative o KEDA permiten la funcionalidad sin servidor.
Knative:
 Knative Serving: escala automáticamente las aplicaciones en función del tráfico. Puede reducirse a cero cuando no hay tráfico.
 Knative Eventing: gestiona arquitecturas basadas en eventos, lo que permite que las funciones se activen en función de eventos externos.
 KEDA (escalado automático basado en eventos de Kubernetes):
 Proporciona un escalado automático para aplicaciones basadas en eventos al escalar automáticamente los recursos en respuesta a eventos externos, como los mensajes en cola o las solicitudes HTTP.
 Características principales de Serverless:
 Escalado automático: escala hacia arriba y hacia abajo en función de la demanda.
 Pago por uso: los cargos se basan en el uso real de los recursos (CPU, memoria, tiempo de ejecución).
 Gestión cero: los desarrolladores se centran en el código, no en la infraestructura subyacente.
Pod Communication
En Kubernetes, la comunicación de pod a pod dentro del mismo nodo tiene las siguientes características:
1. Comunicación directa:
 Los pods del mismo nodo pueden comunicarse directamente entre sí mediante las direcciones IP internas asignadas por la red del clúster.
2. Superposición de red Pod:
 Kubernetes usa una superposición de red (según el complemento de red, como Calico o Flannel) para garantizar que los pods puedan comunicarse entre sí, incluso dentro del mismo nodo.
3. Sin NAT (traducción de direcciones de red):
 Para la comunicación de un pod a otro dentro del mismo nodo, Kubernetes normalmente no requiere la traducción de direcciones de red (NAT). Los pods se comunican directamente mediante sus direcciones IP sin necesidad de traducción.
4. Mismo espacio de nombres de red:
 Los pods que se encuentran dentro del mismo nodo forman parte del mismo espacio de nombres de red, lo que les permite comunicarse entre sí directamente a través de las IP asignadas sin necesidad de equilibrar la carga o enrutamiento externos.
5. Las IP de los pods son únicas en todo el clúster:
 Aunque los pods se ejecuten en el mismo nodo, cada pod tiene una dirección IP única dentro del clúster, lo que garantiza una comunicación clara y directa.
6. Comunicación rápida y eficiente:
 Dado que la comunicación se produce dentro del mismo nodo, generalmente es más rápida y eficiente que la comunicación entre nodos porque evita los saltos de red entre los nodos.
Implementación de aplicaciones sin estado
En Kubernetes, el objeto de implementación es ideal para implementar aplicaciones sin estado. Gestiona réplicas de pods, admite actualizaciones continuas para evitar tiempos de inactividad y ofrece capacidad de recuperación automática y escalabilidad. Las implementaciones son perfectas para las apps sin estado, ya que no necesitan almacenamiento permanente y los Pods se pueden reemplazar o escalar fácilmente según sea necesario.
Etiquetas
En Kubernetes, las etiquetas son clave para administrar los costos mediante la categorización y la organización de los recursos. Puedes asignar etiquetas para agrupar los recursos por proyecto, equipo o entorno, lo que facilita el seguimiento del uso y la asignación de los costos. Los proveedores de servicios en la nube admiten ampliamente las etiquetas con fines de facturación y supervisión.


El comando kubectl logs con el indicador --previous se usa para ver los registros de un contenedor terminado en un pod con varios contenedores en Kubernetes.
Ejemplo:
<pod-name><container-name>kubectl registra -c --previous
Esto se puede abreviar como --p
Ingeniero de confiabilidad del sitio
En un entorno nativo de la nube, el ingeniero de confiabilidad del sitio (SRE) suele ser responsable de administrar los acuerdos de nivel de servicio (SLA), los indicadores de nivel de servicio (SLO) y los objetivos de nivel de servicio (SLO).
Implementaciones y conjuntos de estados
En Kubernetes, las especificaciones de los contenedores de Deployments y StatefulSets son similares en los siguientes aspectos:
1. Plantilla de pod: ambos utilizan una plantilla de pod para definir las especificaciones del contenedor, incluida la imagen del contenedor, los recursos, los puertos, las variables de entorno y los montajes de volumen.
2. Administración de réplicas: ambas permiten definir la cantidad de réplicas (instancias) de los pods.
3. Comportamiento de los contenedores: ambos administran los contenedores dentro de los Pods de la misma manera, asegurándose de que los contenedores se ejecuten según la configuración especificada.
Presupuesto de Pod Disruption
El presupuesto de interrupción de los módulos (PDB) en Kubernetes es un mecanismo que garantiza que haya un número mínimo de pods disponibles durante las interrupciones voluntarias, como las de mantenimiento o actualizaciones. Limita el número de pods que se pueden desalojar o interrumpir simultáneamente.
 Evita el tiempo de inactividad: la PDB ayuda a mantener la disponibilidad de las aplicaciones durante la actualización o desalojo de los nodos.
 Disponibilidad mínima/máxima: puedes especificar la cantidad mínima de pods que deben estar disponibles o la cantidad máxima de pods que pueden interrumpirse a la vez.
 Interrupciones voluntarias: esto se aplica a acciones voluntarias, como drenar los nodos, no a las interrupciones involuntarias, como los bloqueos.
Patrón de sidecar
En Kubernetes, el patrón sidecar consiste en ubicar los contenedores en un pod para proporcionar funciones complementarias, como el registro, la supervisión, el uso de proxy o la seguridad. Los contenedores sidecar amplían o dan soporte al contenedor principal al gestionar tareas como el enrutamiento del tráfico, el procesamiento de datos o la observabilidad.
Cerebro dividido y elección de líderes
La división del cerebro ocurre en los sistemas distribuidos cuando los problemas de red hacen que varios nodos actúen como líderes, lo que genera acciones conflictivas e inconsistencias en los datos. Interrumpe la estabilidad y la coherencia del sistema. Leader Election evita conflictos similares a los de «cerebros divididos» al garantizar que solo una instancia de una aplicación distribuida con estado actúe como líder a la vez.
Espacios de nombres de red
En un pod, los contenedores suelen compartir el espacio de nombres de la red. Esto permite que los contenedores del mismo pod se comuniquen entre sí a través del host local y compartan la misma dirección IP y los mismos puertos. También suelen compartir otros espacios de nombres, como IPC (comunicación entre procesos) y UTS (nombre de host).
OpenID Connect
En el contexto de la autenticación y la autorización, OIDC son las siglas de OpenID Connect. Es una capa de identidad construida sobre el protocolo OAuth 2.0, que se utiliza para verificar la identidad del usuario y permitir una autenticación segura.


Reclamaciones de volumen persistentes
Entre los aspectos importantes de las declaraciones de volumen persistentes (PVC) en Kubernetes se incluyen los siguientes:
1. Proceso de enlace: los PVC son solicitudes de almacenamiento de los usuarios y están enlazados a un volumen persistente (PV) que coincide con el tamaño, el modo de acceso y la clase de almacenamiento solicitados. Una vez que un PVC se vincula a un PV, la relación es exclusiva hasta que se elimine el PVC.
2. Clases de almacenamiento: los PVC pueden especificar una clase de almacenamiento para determinar el tipo de almacenamiento que necesitan (por ejemplo, clases de SSD, HDD o clases específicas de la nube). Si no se especifica ninguna clase, se utilizará la clase de almacenamiento predeterminada del clúster.
3. Modos de acceso:
 ReadWriteOnce (RWO): un solo nodo puede montar el volumen en modo de lectura-escritura.
 ReadOnlyMany (ROX): muchos nodos pueden montar el volumen como de solo lectura.
 ReadWriteMany (RWX): muchos nodos pueden montar el volumen en modo de lectura-escritura.
4. Aprovisionamiento dinámico frente a aprovisionamiento estático:
 Aprovisionamiento dinámico: Kubernetes crea automáticamente un PV cuando se solicita un PVC, en función de la clase de almacenamiento especificada.
 Aprovisionamiento estático: un administrador crea previamente las máquinas fotovoltaicas y las comparan manualmente con ellas en función de los requisitos de almacenamiento.
5. Políticas de reclamación:
 Conservar: conserva la energía fotovoltaica y requiere una intervención manual para recuperar o limpiar el almacenamiento.
 Eliminar: elimina el almacenamiento subyacente cuando se elimina el PVC, que se suele utilizar con volúmenes aprovisionados de forma dinámica.
 Reciclar: limpia el almacenamiento (elimina los datos), pero está obsoleto en favor del aprovisionamiento dinámico.
6. Redimensionamiento del volumen: los PVC se pueden redimensionar de forma dinámica si el almacenamiento subyacente admite el cambio de tamaño y el PVC tiene habilitada la configuración correcta (por ejemplo, habilitar la expansión del volumen en StorageClass).
7. Para permitir el intercambio de datos entre diferentes CronJobs que se ejecutan en diferentes momentos, puedes usar un volumen persistente (PV) y una notificación de volumen persistente (PVC).
Un caso práctico para combinar contenedores de inicio con notificaciones de volumen persistentes (PVC) es inicializar los datos compartidos antes de que se inicie la aplicación principal. Por ejemplo, un contenedor de inicio puede descargar o preparar archivos (por ejemplo, esquemas de bases de datos o scripts de configuración) en un PVC, al que luego accede desde el contenedor principal. Esto garantiza que los datos estén listos y sean consistentes antes de que se ejecute la aplicación, separando las tareas de configuración de la ejecución de la aplicación principal.
Descubrimiento de servicios
Los dos modos principales de descubrimiento de servicios en Kubernetes son:
1. Basado en DNS: los servicios se descubren mediante nombres DNS creados automáticamente.
2. Variables de entorno: los pods obtienen información del servicio mediante variables de entorno predefinidas en el momento de la creación.
Puntos finales de servicio
En Kubernetes, los puntos finales de servicio se utilizan principalmente para representar las ubicaciones de red (direcciones IP y puertos) de los pods que respaldan un servicio específico. Permiten que el servicio dirija el tráfico a las instancias de pod correctas, lo que proporciona una forma de conectar el servicio a los pods que están en ejecución. Los puntos finales de servicio de Kubernetes son recursos que rastrean las ubicaciones de red (direcciones IP y puertos) de los pods que coinciden con el selector de etiquetas de un servicio. Desempeñan un papel clave en la forma en que los servicios dirigen el tráfico a los pods.
1. Asignación de servicios a los pods: los puntos finales proporcionan las direcciones IP y los puertos reales de los pods que hay detrás de un servicio. Cuando se crea un servicio, Kubernetes genera automáticamente un objeto de punto final con las direcciones de todos los pods coincidentes.
2. Actualizaciones dinámicas: a medida que se crean o destruyen los pods, el objeto Endpoint se actualiza de forma dinámica. Esto garantiza que el servicio sepa siempre a dónde enviar el tráfico, lo que refleja el estado actual de los pods.
3. Servicios independientes: en el caso de un servicio independiente (ClusterIP: ninguno), las consultas de DNS del servicio devuelven las direcciones IP de los pods individuales (a través del objeto Endpoints) en lugar de una IP de servicio única. Esto permite la comunicación directa de un pod a otro.
4. Subconjunto de nodos: si un servicio está restringido por selectores o tolerancias de nodos, solo los pods que cumplan con los criterios del servicio aparecerán en el objeto Endpoints.
5. Salud y preparación: Los criterios de valoración tienen en cuenta la preparación de las cápsulas. Los pods que no están listos no aparecen en la lista de terminales, lo que garantiza que el tráfico solo se dirija a los pods en buen estado.
6. Controlador de puntos finales: el controlador de puntos finales de Kubernetes es responsable de actualizar los objetos de punto final asociados a un servicio, manteniéndolos sincronizados con los estados del pod en ejecución.
Uso del espacio de nombres en Kubernetes
 Definición: los espacios de nombres proporcionan una forma de dividir los recursos del clúster entre varios usuarios. Ayudan a administrar y organizar diferentes entornos (por ejemplo, desarrollo, puesta en escena, producción) y a aislar las cargas de trabajo.
 Uso:
<name> Crea con kubectl create namespace.
<name><command> Configure los recursos en un espacio de nombres específico con kubectl --namespace=.
 Los espacios de nombres son útiles en entornos con varios inquilinos en los que diferentes equipos o proyectos comparten un clúster de Kubernetes.
 Espacios de nombres predeterminados: default, kube-system, kube-public.
 Mejores prácticas:
 Use espacios de nombres para segregar entornos y aplicaciones de equipo.
 Utilice el control de acceso basado en roles (RBAC) para administrar el acceso por espacio de nombres.
 Supervise las cuotas de recursos y los rangos de límites dentro de cada espacio de nombres para evitar que se agoten los recursos.
Políticas de seguridad de los módulos (PSP)
 Definición: los PSP son políticas de Kubernetes obsoletas que controlan los aspectos de seguridad de la especificación de un pod.
 Características principales:
 Controle los atributos de seguridad, como la escalación de privilegios, la ejecución como usuario root, el acceso a los espacios de nombres de los hosts y el uso de tipos de volúmenes específicos.
 Defina un objeto de política que especifique qué pods pueden ejecutarse en función de la configuración de seguridad.
 Se aplica mediante controladores de admisión que comprueban las especificaciones de los pods antes de crearlos o actualizarlos.
 Sustitución: los PSP han quedado obsoletos en la versión 1.21 de Kubernetes y se eliminarán en futuras versiones. Sustituya los PSP por mecanismos más modernos, como Open Policy Agent (OPA) o Kyverno para las políticas de seguridad.
 Mejores prácticas:
 Transición de los PSP a herramientas de seguridad más nuevas, como OPA o Kyverno.
 Implemente políticas de seguridad para aplicar las mejores prácticas en diferentes entornos.
Mecanismos de escalado automático de Kubernetes
 Escalador automático de cápsulas horizontales (HPA):
 Ajusta la cantidad de réplicas de pods en función de la CPU, la memoria o las métricas personalizadas.
 Se amplía automáticamente (añade pods) o se amplía (elimina pods) en función de los umbrales de utilización de los recursos.
<threshold><min_replicas><max_replicas> Usa kubectl autoscale deploy <deployment>--cpu-percent= --min= --max= para configurar HPA.
 Escalador automático Vertical Pod (VPA):
 Ajusta las solicitudes y los límites de recursos (CPU, memoria) de un pod en función del uso real.
 Garantiza un rendimiento óptimo del pod y la eficiencia de los recursos al evitar el aprovisionamiento excesivo o insuficiente de los recursos.
 Escalador automático de clústeres:
 Amplía todo el clúster añadiendo o eliminando nodos en función de las demandas pendientes de los pods.
 Supervisa los pods que no se pueden programar debido a la escasez de recursos y ajusta el número de nodos en consecuencia.
 Mejores prácticas:
 Utilice HPA para aplicaciones con cargas de trabajo variables.
 Combine HPA y VPA para un escalado más dinámico.
 Asegúrese de que el clúster tenga suficientes recursos (ajuste de escala automático de nodos) para soportar el escalado de los pods.
Rastreo distribuido
 Definición: el rastreo distribuido ayuda a rastrear el flujo de solicitudes entre los microservicios al proporcionar visibilidad de la interacción entre los componentes de un sistema distribuido.
 Propósito:
 Identifica los cuellos de botella, las latencias y los errores en el rendimiento en todos los servicios.
 Es útil para depurar y optimizar el rendimiento de las aplicaciones nativas de la nube.
 Herramientas clave:
 Jaeger: una herramienta de rastreo distribuido de extremo a extremo de código abierto que se utiliza para monitorear y solucionar problemas de microservicios.
 Zipkin: un sistema de rastreo diseñado para recopilar datos de temporización y visualizarlos para solucionar problemas de latencia.
 OpenTelemetry: un marco de observabilidad independiente del proveedor para generar, recopilar y administrar datos de telemetría, como trazas, registros y métricas.
 Conceptos:
 Rastreo: una solicitud completa de principio a fin en varios microservicios.
 Intervalo: segmento de una traza que representa una sola unidad de trabajo (p. ej., una llamada a la API).
 Propagación del contexto: transferencia del contexto del rastreo entre servicios para seguir el ciclo de vida de una solicitud.
 Mejores prácticas:
 Utilice el rastreo distribuido para monitorear el rendimiento de los microservicios en tiempo real.
 Integre el rastreo con el registro y las métricas para una estrategia de observabilidad holística.
 Concéntrese en las transacciones comerciales clave para garantizar unas operaciones de servicio fluidas.
Automatizar las implementaciones utilizando los principios de GitOps
 Definición: GitOps es un enfoque moderno del despliegue continuo (CD) que utiliza Git como fuente única de información fiable para la gestión declarativa de infraestructuras y aplicaciones.
 Conceptos clave:
 Configuración declarativa: las configuraciones de la infraestructura y las aplicaciones se definen en código y se almacenan en Git.
 Git como fuente de la verdad: todas las configuraciones y cambios de implementación se administran a través de Git. Las confirmaciones de Git representan actualizaciones del estado deseado.
 Implementación basada en extracciones: los agentes automatizados supervisan continuamente el repositorio de Git y se aseguran de que el clúster refleje el estado declarado en Git. Para implementar GitOps se utilizan herramientas como ArgoCD y Flux.
 Ventajas:
 Auditabilidad: Git rastrea todos los cambios en la infraestructura y las aplicaciones, proporcionando un registro de auditoría claro.
 Control de versiones: cada cambio se puede rastrear, revertir o volver a aplicar utilizando el historial de Git.
 Automatización: las canalizaciones de implementación se activan automáticamente cuando los cambios se envían al repositorio.
 Mejores prácticas:
 Mantenga las configuraciones de infraestructura y aplicaciones versionadas en Git.
 Usa herramientas como ArgoCD o Flux para automatizar la reconciliación entre los clústeres de Git y Kubernetes.
 Refuerce la seguridad y la gobernanza mediante la implementación de procesos de revisión (por ejemplo, solicitudes de cambios) antes de incorporar los cambios a la producción.
Infraestructura como código (IaC)
 Definición: la IaC es la práctica de administrar y aprovisionar la infraestructura mediante código en lugar de mediante procesos manuales. Esto permite automatizar la configuración, el escalado y la administración de los recursos de la nube, lo que garantiza la coherencia y la repetibilidad.
 Herramientas clave:
 Terraform: herramienta independiente de la nube para aprovisionar y administrar la infraestructura en múltiples plataformas (AWS, Azure, GCP, etc.).
 CloudFormation: herramienta de IaC específica de AWS para crear y administrar los recursos de AWS mediante plantillas declarativas.
 Pulumi: permite el uso de lenguajes de programación de uso general (Python, Go, etc.) para definir la infraestructura.
 Ventajas:
 Coherencia: la configuración se escribe una vez y se aplica de manera uniforme en todos los entornos (desarrollo, puesta en escena, producción).
 Control de versiones: dado que la infraestructura se trata como un código, se puede versionar y auditar con herramientas como Git.
 Escalabilidad: iAC facilita la ampliación o reducción de la infraestructura en función de los parámetros definidos.
 Mejores prácticas:
 Mantenga el código de infraestructura modular y reutilizable.
 Almacene el IaC en repositorios de control de versiones (por ejemplo, Git).
 Usa revisiones de código y canalizaciones de automatización para aplicar los cambios en la infraestructura.
Estrategias de implementación
 Implementaciones azul-verdes:
 Definición: en esta estrategia, se utilizan dos entornos de producción idénticos (azul y verde). Un entorno (azul) ejecuta la versión actual de la aplicación, mientras que la nueva versión se implementa en el otro entorno (verde).
 Cómo funciona:
 Implemente la nueva versión en un entorno ecológico.
 Cambie el tráfico de azul a verde (normalmente mediante balanceadores de carga o cambios en el DNS).
 Si no se detecta ningún problema, el azul se convierte en el entorno de espera para la próxima actualización.
 Ventajas:
 Sin tiempo de inactividad durante la implementación.
 Fácil reversión a la versión anterior si surgen problemas.
 Lanzamientos en Canary:
 Definición: Una versión estándar es una estrategia de implementación en la que se lanza una nueva versión de la aplicación para un pequeño subconjunto de usuarios antes de implementarla por completo para todos los usuarios.
 Cómo funciona:
 Implemente la nueva versión para una pequeña porción de usuarios (entorno canario).
 Supervise el rendimiento y el comportamiento.
 Aumente gradualmente el tráfico a la nueva versión si no surgen problemas, o retroceda si se detectan problemas.
 Ventajas:
 Minimiza el riesgo al permitir realizar pruebas en el mundo real en un segmento pequeño de usuarios.
 Proporciona comentarios tempranos y ayuda a garantizar la estabilidad.
 Mejores prácticas:
 Elija implementaciones de color azul y verde cuando necesite actualizaciones sin tiempo de inactividad con reversiones rápidas.
 Utilice las versiones de Canary para realizar despliegues incrementales y controlar mejor las implementaciones.
Políticas de red en Kubernetes
 Definición: las políticas de red de Kubernetes controlan el flujo de tráfico a nivel de dirección IP o puerto dentro del clúster. Definen cómo los pods pueden comunicarse entre sí y con los terminales externos.
 Componentes clave:
 Selector de pods: define a qué pods se aplica la política de red.
 Reglas de ingreso: controla qué tráfico puede entrar en un pod.
 Reglas de salida: controla el tráfico que puede enviar un pod.
 Uso:
 De forma predeterminada, se permite todo el tráfico entre los pods. Puede restringir esto definiendo políticas de red.
 Las políticas de red utilizan etiquetas para seleccionar los pods afectados y se aplican tanto al tráfico de entrada como al de salida.
 Mejores prácticas:
 Siga el principio del mínimo privilegio: permita solo el tráfico necesario y bloquee todo lo demás.
 Utilice las etiquetas de forma eficaz para aplicar las políticas de red de forma detallada.
 Audite y pruebe regularmente las políticas de red para garantizar la seguridad y la funcionalidad.
Service Mesh Security
 Definición: una malla de servicios es una capa de infraestructura que gestiona la comunicación entre microservicios. Proporciona observabilidad, gestión del tráfico y seguridad (por ejemplo, TLS mutuo o control de acceso) para la comunicación de servicio a servicio.
 Características principales:
 TLS mutuo (mTLS): cifra la comunicación de servicio a servicio y verifica la identidad de ambas partes en la comunicación.
 Autorización y aplicación de políticas: permite establecer políticas detalladas para controlar qué servicios pueden comunicarse.
 Cifrado del tráfico: garantiza la transmisión segura de datos entre los servicios al cifrar el tráfico automáticamente.
 Herramientas comunes de Service Mesh:
 Istio: ofrece funciones de seguridad como el TLS mutuo, el cifrado de tráfico y el RBAC.
 Linkerd: se centra en la simplicidad y el rendimiento, con sólidas funciones de seguridad, como el cifrado TLS automático.
 Cónsul: proporciona detección de servicios, configuración y comunicación segura entre servicios.
 Mejores prácticas:
 Implemente un TLS mutuo para proteger la comunicación de servicio a servicio.
 Utilice las funciones de observabilidad de la malla de servicios para monitorear los patrones de comunicación y detectar cualquier vulnerabilidad de seguridad.
 Defina políticas de control de acceso estrictas para garantizar que solo los servicios autorizados puedan comunicarse.
Administración de secretos
 Definición: La administración de secretos implica almacenar y acceder de forma segura a información confidencial, como las claves de API, las contraseñas y los certificados.
 Secretos de Kubernetes:
 Kubernetes proporciona un objeto secreto para almacenar información confidencial, como tokens y credenciales.
 Los secretos pueden montarse como volúmenes o exponerse como variables de entorno en pods.
 Mejores prácticas para gestionar los secretos:
 Utilice el cifrado: almacene siempre los secretos en un formato cifrado. Kubernetes admite el cifrado de los secretos en reposo.
 Limitar el acceso: utilice el control de acceso basado en roles (RBAC) para restringir el acceso a los secretos. Solo los servicios que necesitan el secreto deben tener acceso.
 Evite codificar los secretos de forma rígida: nunca codifique datos confidenciales en el código de la aplicación o en los archivos de configuración.
 Herramientas clave para la gestión de secretos:
 HashiCorp Vault: una herramienta para almacenar y administrar de forma segura el acceso a los secretos. Proporciona secretos dinámicos, rotación de claves y registros de auditoría.
 AWS Secrets Manager y Azure Key Vault: servicios nativos de la nube que permiten el almacenamiento, la recuperación y la rotación seguros de los secretos.
 Secretos sellados: cifra los secretos de Kubernetes para garantizar que estén seguros cuando se almacenan en sistemas de control de versiones como Git.
 Mejores prácticas:
 Utilice herramientas como HashiCorp Vault o Sealed Secrets para garantizar una gestión segura de los secretos en Kubernetes.
 Cambie los secretos con regularidad para minimizar el impacto de los posibles compromisos.
 Asegúrese de que los secretos estén cifrados tanto en reposo como en tránsito.
Estándares de seguridad para cápsulas (PSS) en Kubernetes
 Definición: los estándares de seguridad de los pods (PSS) definen la configuración de seguridad a nivel de pod para ayudar a aplicar las mejores prácticas de seguridad en los clústeres de Kubernetes. El PSS se introdujo como sustituto de las obsoletas políticas de seguridad de los pods (PSP).
 Admisión de seguridad al Pod:
 Kubernetes 1.22 presentó un nuevo controlador de admisión Pod Security para aplicar el PSS, que clasifica los pods en tres niveles:
1. Privilegiado: no se aplican restricciones. Se usa para módulos confiables que requieren muchos permisos, como los componentes de infraestructura.
2. Base de referencia: aplica las mejores prácticas de seguridad básicas, como evitar la escalada de privilegios o actuar como usuario raíz.
3. Restringido: aplica políticas de seguridad más estrictas, como prevenir los volúmenes de rutas de host y aplicar contextos de seguridad más estrictos.
 Cómo usarlo:
 Las etiquetas de los espacios de nombres se utilizan para hacer cumplir las políticas de seguridad. Los pods de un espacio de nombres específico deben cumplir los estándares de seguridad aplicados.
 Aplica políticas de seguridad en función de las cargas de trabajo y su nivel de sensibilidad (por ejemplo, las cargas de trabajo de producción deben estar en modo restringido).
 Mejores prácticas:
 Utilice el modo restringido para cargas de trabajo críticas a fin de garantizar el entorno más seguro.
 Evite utilizar contenedores privilegiados a menos que sea absolutamente necesario.
 Audite regularmente las configuraciones de los módulos y cumpla con los estándares de seguridad de los módulos para reducir las superficies de ataque.
Dominio: entrega de aplicaciones nativas en la nube


