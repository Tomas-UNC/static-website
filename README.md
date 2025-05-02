Proyecto: Entorno de desarrollo Kubernetes con Minikube

Este repositorio contiene los manifiestos de Kubernetes necesarios para desplegar un entorno de desarrollo local que sirve contenido estático desde un sitio web personalizado. Este trabajo forma parte de la 
actividad 0311AT de la materia *Computación en la Nube* del ITU - UNCuyo.

Estructura del proyecto

- `pv.yaml`: Define un volumen persistente local.
- `pvc.yaml`: Reclama el volumen para el pod.
- `deployment.yaml`: Despliega una instancia de NGINX que sirve contenido HTML desde el volumen.
- `service.yaml`: Expone el pod mediante un servicio de tipo NodePort.

Pasos para reproducir este entorno

1. Prerrequisitos

- Tener instalado:
  - [Git](https://git-scm.com/)
  - [Minikube](https://minikube.sigs.k8s.io/)
  - [kubectl](https://kubernetes.io/docs/tasks/tools/)

2. Clonar los repositorios necesarios

Repositorio del sitio web
- bash
git clone https://github.com/TU_USUARIO/static-website.git

Repositorio de manifiestos Kubernetes

`
git clone https://github.com/TU_USUARIO/k8s-manifests.git
cd k8s-manifests
`

Levantar el clúster de Minikube

`
minikube start --driver=docker
`

Aplicar los manifiestos

`
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
`

Verificar que todo esté funcionando

`
kubectl get all
`

Acceder al sitio web desde el navegador

`
minikube service web-service
`

Repositorios Publicos

`
https://github.com/Tomas-UNC/static-website/tree/master

`
