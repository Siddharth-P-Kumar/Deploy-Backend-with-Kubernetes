<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy Backend with Kubernetes

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks4)

**Author:** siddharthpk nextwork  
**Email:** siddharthpknextwork@gmail.com

---

## Deploy Backend with Kubernetes

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks4_6cfb382f2)

---

## Introducing Today's Project!

In this project, I will deploy a backend application on a Kubernetes cluster using kubectl and track its deployment with Amazon EKS, because it's the final step in the Kubernetes with AWS series and will solidify my understanding of application deployment.

### Tools and concepts

I used Kubernetes, ECR, kubectl, and Docker to build a container image of my backend application, push it to ECR, and then deploy it to my EKS cluster. Key concepts include using Deployment and Service manifests to define how Kubernetes manages and exposes my application, and verifying the deployment through the EKS console.

### Project reflection

This project took me approximately 2 hours. The most challenging part was setting up the correct IAM access policies to interact with the EKS console, but my favourite part was visually confirming the successful deployment of my application by inspecting the Pod events in the console.

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. The cluster's role in this deployment is to provide the underlying infrastructure for running and managing my containerized backend application, ensuring scalability, high availability, and efficient resource utilization.

### Backend code

I retrieved backend code by cloning the GitHub repository to my EC2 instance. Pulling code is essential to this deployment because it provides the application source code needed to build the Docker image and deploy the backend application to Kubernetes.

### Container image

Once I cloned the backend code, I built a container image because Kubernetes needs to pull the application from a container image that it can access. Without an image, it would be difficult for Kubernetes to reliably create and manage multiple, consistent instances of my application.

I also pushed the container image to a container registry, which is Amazon Elastic Container Registry (ECR). ECR facilitates scaling for my deployment because it allows Kubernetes to quickly spin up extra identical containers running my app in seconds when traffic spikes, by pulling the latest image on demand.

---

## Manifest files

Kubernetes manifests are files that tell Kubernetes how to run your application in a cluster, acting as blueprints that define the desired state of your app. Manifests are helpful because they allow Kubernetes to automatically set up and manage your application, ensuring consistent and repeatable deployments without manual configuration.

A Deployment manifest manages how Kubernetes runs and maintains your application, including how many copies to run and resource limits. The container image URL in my Deployment manifest tells Kubernetes where to pull the container image from when it deploys your application.

A Service resource exposes your application and routes traffic to it. My Service manifest sets up how Kubernetes will make my application accessible and direct incoming requests.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks4_b01876554)

---

## Backend Deployment!

To deploy my backend application, I installed kubectl and used it to apply my Deployment and Service manifest files.

### kubectl

kubectl is the command-line tool for interacting with Kubernetes resources once your cluster is running. I need this tool to apply my manifests and deploy my application. I can't use eksctl for the job because eksctl is used for setting up and deleting the EKS cluster, while kubectl is specifically for deploying applications and managing resources within the cluster.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks4_6cfb382f2)

---

## Verifying Deployment

My extension for this project is to use the EKS console to visually inspect my EKS cluster and confirm the successful deployment of my backend application. I had to set up IAM access policies because they are essential for

Once I gained access into my cluster's nodes, I discovered pods running inside each node. Pods are Kubernetes’ smallest work unit. Think of it as one or more containers that run side by side. Containers in a pod share the same network address, so Kubernetes can manage them as a single piece.

The EKS console shows you the events for each pod, where I could see events confirming the successful creation and running of my backend application's containers. This validated that my Deployment and Service manifests were correctly applied and my application is active within the cluster.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks4_3b391f873)

---

---
