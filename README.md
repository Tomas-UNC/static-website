Proyecto Kubernetes: Sitio Web Estático con NGINX

Este proyecto despliega un sitio web estático usando un contenedor NGINX en Minikube, con un volumen persistente para servir archivos estáticos.

Requisitos

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- Docker (para entorno local si usás el driver Docker)
- Git

Instalación de Minikube

1. Instalar Minikube desde la web oficial:  
   👉 https://minikube.sigs.k8s.io/docs/start/

2. Iniciar Minikube (usando el driver Docker en Windows):

bash
minikube start --driver=docker

1. Repositorio con los manifiestos de Kubernetes:

git clone https://github.com/tu-usuario/k8s-manifests.git
cd k8s-manifests

2. Repositorio con el sitio estático:

git clone https://github.com/tu-usuario/static-site.git

Aplicar los Manifiestos

kubectl apply -f persistent-volume.yaml
kubectl apply -f persistent-volume-claim.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

Estructura de Archivos

ersistent-volume.yaml = Define un volumen persistente local.
persistent-volume-claim.yaml = Reclama el volumen anterior.
deployment.yaml = Despliega el contenedor NGINX y monta el volumen.
service.yaml = Expone el contenedor como servicio de tipo NodePort.

Acceder al Sitio Web

Después de aplicar los manifiestos, ejecutá:
minikube service static-web-service --url

Esto te devolverá una URL como:
http://127.0.0.1:60892/

Tomas Beltran
