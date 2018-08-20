# Helm tutorial

## Overview

In tutorial I will give you brief introduction to [Helm](https://www.helm.sh).  You might ask, what is Helm? Simply put helm is a Kubernetes package manager.  Sort of like `apt-get` or `yum` but for Kubernetes. 

This project is similar to [hello-docker-deployment](https://github.com/saurin-tech/hello-docker-deployment).  I highly recommend that you go read that first to understand what we will be creating in this project.  Just like in the project mentioned above you will be creating a single service and a simple pod which has a spring boot application running inside of it.

## My setup 

- Host OS: Ubuntu 18.04
- Docker: 18.06.0-ce
- Minikube: 0.28.2
- Kubectl: 
    - Client version: 1.11.2
    - Server version: 1.10.0
- Helm:
    - Client version: 2.9.1
    - Server version: 2.9.1

If you are running linux do not use snap to install helm.  Snap install is having issues when installing helm.  Instead of using snap install helm manually.  [Instructions to install helm manually](https://github.com/snapcrafters/helm/issues/10).

## How to run

- Once helm is installed go ahead and run `helm init` which will install tiller on the minikube.

- After tiller is up and running in the minikube execute `helm install ./hello-docker-chart` this will install the chart with in the minikube.

- To test to see if the chart is properly installed and the application is up find the IP for minikube by typing `minikube ip`.

- execute `<minikubeip>:30001/hello` inside of a browser to see the results.  

- To delete the deployment `helm delete --purge <Release Name>`

## About Helm

- Helm uses templating engine from GO with it's own flare.  Inside of the templates directory you will find `yaml` files that hold configurations for various types of Kubernetes objects.  You can also do interpolation and fetch values from the `values.yaml` file as well.  Compare the `deployment.yaml` and `service.yaml` file in this project with the `hello-docker-deployment.yml` and `hello-docker-svc.yml` in the hello-docker-deployment project to see the differences and similarities.  Visit [Helm Docs](https://docs.helm.sh/chart_template_guide/#the-chart-template-developer-s-guide) to learn how to create your own templates.

## Commands used to create this tutorial

- To create chart using helm CLI
    
    - `helm create <hello-docker-chart>`

- To initalize Helm

    - `helm init`

- To render chart by using tiller

    - `helm install --debug --dry-run ./<hello-docker-chart>`

- To install chart

    - `helm install <./hello-docker-chart>`

- To delete chart

    - `helm delete --purge <Release Name>`