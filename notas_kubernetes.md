# Kubernetes

Un orquestador permite manejar aplicaciones dentro de contenedores Docker a través de muchos servidores físicos o virtuales.

Kubernetes es una herramienta de orquestación de contenedores desarrollada por Google y es Open Source.

Además de permitir manejar muchos contenedores a través de muchos nodos, Kubernetes también ofrece alta disponibilidad a través de la creación de réplicas de una aplicación y reduce el *down time*, ya que si una de esas réplicas deja de funcionar, kubernetes redirigirá el tráfico a una réplica que esté disponible. También permite escalar copias en caso de ser necesario.

## Arquitectura de Kubernetes

Básicamente, kubernetes se divide en dos grupos: los masters y los workers.

En los master se ejecutan los siguientes componentes:

* La **API Server**: expone la interfaz para que diferentes clientes puedan interactuar con kubernetes, como puede ser una interfaz web, otros clientes API o el cliente API de kubernetes que es **kubectl**. 
* El **Controller Manager** gestiona lo que ocurre en el cluster; se encarga de controlar qué contenedores están corriendo y cuáles deberían estar corriendo. Si uno de los workers falla, kubernetes lo detecta y se encarga de mover
el/los contenedores a otro nodo para tratar de cumplir con lo definido
en el manifiesto.
* El **Scheduler** recibe las ordenes del controller manager y mueve los pods de nodo en nodo.
* El **etcd** es la base de datos que almacena toda la información y toda la configuración del cluster, así como su estado.

Cada worker ejecuta un agente de kubernetes denominado **kubelet**. En los workers o nodos es donde se van a ejecutar los pods, que contienen los contenedores donde corre una aplicación. Por su parte, el **kube-proxy** es un proxy de red que implementa los servicios de red de Kubernetes en cada nodo.

## Pods

Un pod es un set de contenedores que comparten el namespace de red, es decir, tienen la misma ip. Normalmente, en cada pod corre un sólo contenedor, pero si es necesario, se puede dividir una tarea en varios contendores.

Su principal característica es que estos pods son volátiles. Así, por ejemplo, cuando se hace un deploy para desplegar una nueva versión, los pods se destruyen y se crean nuevos pods.

## Networking

A través de todos los nodos existe una **overlay network** que permite la comunicación entre todos los pods. Es, básicamente, una red virtual de nodos y enlaces lógicos que se construyen sobre una red existente.

Dado que los pods son volátiles, no es buena idea apuntar directamente a un pod. Por ello, se crean los **servicios**. De esta forma, en lugar de ir de un pod a otro, apuntamos a los servicios, que tienen como backend los pods que corren una aplicación. Hay varios tipos, pero los más comunes son los denominados:

* **cluster IP**, que se caracterizan por tener una ip que nunca cambia.
* **Ingress**, permite crear reglas de acceso
* **Load Balancer**, permite crear un balanceador de carga.
* **Node Port**, permite crear un puerto para llegar a una aplicaciń.

## Manifiestos

Kubernetes se gestion con manifiestos declarativos. Mediante la creación de un manifiesto, definimos los contenedores a levantar y las réplicas necesarias. Un **deployment** es un template para crear pods. la API de kubernetes se encarga de gestionar lo definido en el manifiesto distribuyéndolo entre los workers existentes.

Los servicios de kubernetes, en especial el "scheduler", que se encargan
de gestionar los contenedores, moviéndolos de un worker a otro. La API
de kubernetes se conecta con los worker a través del agente "kubelet".

* **kubeconfig** es el archivo donde están declarados todos los contextos, que son
los cluster de kubernetes definidos. --> kubectl config get-contexts

* **Namespace**: es una división lógica del cluster de kubernetes. Permite separar
la carga o tráfico en el cluster --> kubectl get ns
Todos los contenedores que corren dentro de un pod están en el mismo namespace,
por lo que, tienen la misma ip.

## Links

* Pelado nerd:
  * [KUBERNETES 2021 - De NOVATO a PRO! (CURSO COMPLETO)](https://www.youtube.com/watch?v=DCoBcpOA7W4&t=2540s)
  * [Lens](https://www.youtube.com/watch?v=DFMKcR4BqwM&t=0s)
  * [Minikube](https://minikube.sigs.k8s.io/docs/start/)
  * [Kind](https://kind.sigs.k8s.io/)
  * [Supervisord](https://www.youtube.com/watch?v=mfXnqHRT8hI&t=0s)
  * [Helm](https://www.youtube.com/watch?v=CPjfb-I_BKU&t=0s)
  * [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)
  * [KubeSealed](https://www.youtube.com/watch?v=YuKAiy0Olc0&t=0s)
  * [ENV (Variables de Entorno)](https://www.youtube.com/watch?v=T7lRHHa4YxE&t=0s)
  * [Repositorio github kubernetes](https://github.com/pablokbs/peladonerd/tree/master/kubernetes/35)

## Libros

* [Site Reliability Engineering](https://landing.google.com/sre/book.html)
