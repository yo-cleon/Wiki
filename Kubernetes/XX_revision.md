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
