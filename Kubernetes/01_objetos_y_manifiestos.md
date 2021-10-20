# Objetos y Manifiestos

## Objetos de Kubernetews

Los Objetos son entidades persistentes que Kubernetes utiliza para respresentar el estado de su cluster. Específicamente, puede describir:

- Qué aplicaciones corren en contenedores (y en qué nodos).
- Los recursos disponibles para dichas aplicaciones.
- Las políticas acerca de cómo dichas aplicacioens se comportan (políticas de reinicio, actualización...).

Un objeto es un "registro de intención". Al crear un objeto, en realidad le estás diciendo al sitema de Kubernetes cómo quieres que sea la carga de trabajo del cluster, esto es, el **estado deseado** del cluster.

Cada objeto de Kubernetes incluye dos campos como objetos anidados que determinan la configuración del objeto:

1. El campo **spec**, que es obligatorio, describe el estado deseado del objeto, esto es, las características que quieres que tenga el objeto.
2. El campo **status** describe el estado actual del objeto, y se suministra y actualiza directamente por el sistema de Kubernetes. En cualquier momento, el Plano de Control de Kubernetes gestiona de forma activa el estado actual del objeto para que coincida con el estado deseado requerido.

Al crear un objeto, debemos especificar la spec del objeto que describe su estado deseado, así como información básica del mismo (como el nombre). Cuando usas la API de Kubernetes para crear el objeto (bien de forma directa o usando kubectl), dicha petición a la API debe incluir toda la información en formato JSON en el cuerpo de la petición. A menudo, esta información a kubectl se proporciona como un archivo .yaml, que son los denominados **manifiestos**. kubectl convierte esa información a JSON cuando realiza la llamada a la API.

## Manifiestos

Un manifiesto es básicamente una "descripción de objeto API" de Kubernetes, que especifica el estado deseado de un objeto que Kubernetes mantendrá cuando aplique el manifiesto. Cada archivo de configuración puede contener varios manifiestos.

El manifiesto incluye instrucciones en un archivo yaml o json que especifican cómo desplegar una aplicación al nodo o nodos en un cluster de Kubernetes. Las instrucciones incluyen información sobre el despliegue de Kubernetes, el servicio Kubernetes y otros objetos de Kubernetes que se crearán en el cluster. También se suele hacer referencia al manifiesto como especificación de pod o como archivo deployment.yaml (aunque se permiten otros nombres de archivo). Los parámetros que se deben incluir en un archivo de manifiesto de Kubernetes se describen en la documentación de Kubernetes.

El manifiesto, obligatoriamente, tendrá que indicar los valores de los siguientes campos (como mínimo):

- **apiVersion**: qué versión de la API de Kubernetes estás usando para crear este objeto.
- **kind**: qué clase de objeto quieres crear.
- **metadata**: datos que permiten identificar unívocamente al objeto, incluyendo una cadena de texto para el *name*, *UID*, y opcionalmente el *namespace*.

El formato del campo spec es diferente según el tipo de objeto de Kubernetes, y contiene campos anidados específicos de cada objeto. La Referencia de la API de Kubernetes puede servir de ayuda para encontrar el formato de la spec para cada uno de los objetos que se puede crear usando Kubernetes.

## Pods

Un Pod es el objeto más simple y pequeño de Kubernetes y representa una sola instancia de la aplicación. Un Pod es una colección de uno o más contenedores, con almacenamiento/red compartidos y unas especificaciones de cómo ejecutar los contenedores. En otras palabras, un Pod modela un "host lógico" específicao de la aplicación: contiene uno o más contenedores de aplicacioens relativamente entrelazados.

El contexto compartido de un Pod es un conjunto de namespaces de Linux, cgroups y, potencialmente, otras facetas de aislamiento, las mismas cosas que aíslan un contenedor Docker. Dentro del contexto de un Pod, las aplicaciones individuales pueden tener más subaislamientos aplicados.

Los contenedores dentro de un Pod comparten dirección IP y puerto, y pueden encontrarse a través de localhost. También pueden comunicarse entre sí mediante comunicaciones estándar entre procesos, como semáforos de SystemV o la memoria compartida POSIX. Los contenedores en diferentes Pods tienen direcciones IP distintas y no pueden comunicarse por IPC sin configuración especial. Estos contenedores normalmente se comunican entre sí a través de las direcciones IP del Pod.

Las aplicaciones dentro de un Pod también tienen acceso a volúmenes compartidos, que se definen como parte de un Pod y están disponibles para ser montados en el sistema de archivos de cada aplicación.

Los Pods se consideran entidades relativamente efímeras (en lugar de duraderas). Los Pods se crean, se les asigna un identificador único (UID) y se planifican en nodos donde permanecen hasta su finalización (según la política de reinicio) o supresión. Si un nodo muere, los Pods programados para ese nodo se programan para su eliminación después de un período de tiempo de espera. Un Pod dado (definido por su UID) no se "replanifica" a un nuevo nodo; en su lugar, puede reemplazarse por un Pod idéntico, con incluso el mismo nombre si lo desea, pero con un nuevo UID.

## Links

- [Conceptos de Container Engine y Kubernetes](https://docs.oracle.com/es-ww/iaas/Content/ContEng/Concepts/contengclustersnodes.htm)
- [Entender los Objetos de Kubernetes](https://kubernetes.io/es/docs/concepts/overview/working-with-objects/kubernetes-objects/)
- [Pods](https://kubernetes.io/docs/concepts/workloads/pods/)
- [¿Qué es un Pod](https://kubernetes.io/es/docs/concepts/workloads/pods/pod/)
