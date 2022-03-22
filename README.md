# ArgoCD Repository for ICX Deployment

## Features

This repository uses Helm to deploy ICX applications having the following elements:

* GlobalAnswerFile Secret - Stores the ICX answer file as a secret within Kubernetes. The secret is mounted in the 
    file system and made available to pods. The answer file will eventually become a template and all secret values
    will be managed as AWS Secrets Manager secrets and injected through environment variables.
* Connectionstring Secret - Demonstrates using and AWS Secrets Manager secret that is made available as a Kubernetes 
    secret and injected into pods as an environment varibale.
* ASM Deployment - Includes replicaset to manage multiple ASM replicas and startup, readiness and liveness probes.
* ASM Service - Provides a load balancer and exposes ASM pod replicas to the outside world. Integrated with AWS 
    elastic load balancer.
* PSM Deployment - Includes replicaset to manage multiple PSM replicas and startup, readiness and liveness probes.
* PSM Service - Provides a load balancer and exposes PSM pod replicas to the outside world. Integrated with AWS 
    elastic load balancer.
* BSM Deployment - Includes replicaset to manage multiple BSM services and independent replicas for each service.

## How to deploy an environment?

Run the following commands on your ArgoCD-enabled Kubernetes cluster to deploy an environment.

* Sample "Development" environment:
    ```
    kubectl.exe apply -f https://raw.githubusercontent.com/mariusjacobs/icx-argocd/dev/application-dev.yaml
    ```

* Sample "Staging" environment:
    ```
    kubectl.exe apply -f https://raw.githubusercontent.com/mariusjacobs/icx-argocd/staging/application-staging.yaml
    ```

* Sample "Production" environment:
    ```
    kubectl.exe apply -f https://raw.githubusercontent.com/mariusjacobs/icx-argocd/master/application-prod.yaml
    ```

