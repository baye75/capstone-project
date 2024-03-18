# Sock Shop : A Microservice Demo Application

The sock shop application is the user-facing part of an online shop that sells socks which is intended to aid the demonstration and testing of microservice and cloud native technologies.

## Objective of the Project

The aim of this project is to deploy the the sock shop application using a modern approach that emphasizes automation and efficiency. The goal is to use Infrastructure as a Code (IaaC) for a quick, reliable, and secure deployment on Kubernetes so as to create a reproducible and maintainable deployment that uses modern DevOps practices and tools.

## Resources

The sock shop Microservices Demo is gotten from a GitHub repository at https://github.com/microservices-demo/microservices-demo.github.io while a detailed implentation guide is available at https://github.com/microservices-demo/microservices-demo/tree/master. 

## Requirements and Tools used for the Project

This set up has been made to run in a Linux environment, hence a shell script, named installer.sh has been included in the folders layout to helps install and set up all the dependencies required to successfully execute the project, which include unzip, terraform, kubectl, aws cli, helm, and Jenkins. The unzip command is needed to extract an archived file in Linux. Terraform is needed to run our Terraform configurations. Kubectle is needed to needed to run our Kubernetes commands. The aws cli is needed to set up our AWS environment. Helm, which is somtimes called package manager for Kubernetes is used to manage Kubernetes applications and finally, Jenkins, which is the Continuous Integration Continuous Deployment (CI/CD) tool used in this project, is an open source automation server used to reliably build, test and deploy software.

## Folder Structure

The GitHub repository that contains this project is named capstone-project and it is available in the master branch of the GitHub repository https://github.com/baye75/capstone-project. It contains three major folders namely eks, kubernetes, and assets and four files namely installer.sh (which we described above), cluster-Jenkinsfile, Jenkinsfile, and README.md.

### The eks Folder

The eks folder contains Terraform configuration files for the creation of an Elastic Kubernetes cluster in AWS (Amazon Web Services). A modulalried approach was used to create an EKS (Elastic Kubernetes Service) cluster, a VPC (virtual private cloud), a node group for the cluster which consist of two t2.xlarge EC2 (Elastic Compute Cloud) instances, and IAM (Identity and Access Management) roles for the cluster and the node groups.

### The kubernetes Folder

This folder contains four sub-folders namely micro-service, prometheus-helm, ingress-rule, and nginx-controller.
The micro-service folder contains Terraform configuration files for the deployment of each of the various sections of the sock shop application and the associated services. This include the carts, catalogue, front-end of the application, orders, payment, shipping, user data, rabbbitmq, session database, and all the associated services and databases.
The prometheus-helm folder contains Terraform configuration files for the creation of helm_release resource.As we mentioned earlier, helm helps us manage Kuernetes applications. The helm chart helps us define, install, and upgrade even very complex Kubernetes applications. A chart is a helm package which contains all the resource definitions necessary to run an application inside a Kubernetes cluster. A release is an instance of a chart running inside a Kubernetes cluster.
The nginx-controller folder contains Terraform configuration files that defines the parameters for Ingress-nginx and also Route53 hosted zone. The Ingress-nginx is an Ingress controller for Kubernetes which uses Nginx webserver as areverse proxy and a load balancer. A domain name, "muhammadbaye.me" which was previously obtained from the Namecheap domain providers was hosted using Amazon Route 53, with the configurations provided.
The ingress-rule folder contains Terraform configuration files that Ingress rules for the sock shop application and also prometheus-grafana into the hosted zone. The sock shop application is hosted as a subdomain under the domain name at "sock-shop.muhammadbaye.me".

## Deployment Platform

The Continuous Integration Continous Delivery (CI/CD) platform used is Jenkins. As mentioned earlier, Jenkins is an automation server which enables developers to reliably build, test, and deploy software/applications. Two Jenkinsfiles have been used in this project to automate the deployment of the sock shop application. The first one is named "cluster-Jenkinsfile" and it is used to deploy the creation of our Kubernetes cluster, which have been confiured using the configuration files in the eks folder. This cluster-Jenkinsfile also sets our environments by configuring our AWS credentials so that Jenkins can communicate with AWS. Parameters were also set to be able to create and destroy the cluster with just a click when you select to build with paramters.
The second Jenkinsfile is named "Jenkinsfile" also sets the environment by configuring the AWS credentials. Then it has four "create" stages to automate the deployment of the four sub-folders under the "kubernetes" folder mentioned earlier. Four stages of "destroy" have also been set to enable the infrastructure to be easily destroyed with a click. 

## Visualizing the Application

The sock shop application can be viewed at http://sock-shop.muhammadbaye.me and the grafana metrics can be viewed at http://grafana.muhammadbaye.me

## Screenshots

Attached below are screenshots of the deployment process, the running application and the grafana analytics and motoring page.

![alt text](assets/jenkins1.png)
![alt text](assets/jenkins2.png)
![alt text](assets/jenkins3.png)
![alt text](assets/jenkins4.png)
![alt text](assets/jenkins5.png)
![alt text](assets/jenkins6.png)
![alt text](assets/jenkins7.png)
![alt text](assets/jenkins8.png)

![alt text](assets/socks1.png)
![alt text](assets/socks2.png)
![alt text](assets/socks3.png)
![alt text](assets/socks4.png)
![alt text](assets/socks5.png)
![alt text](assets/socks6.png)

![alt text](assets/grafana1.png)
![alt text](assets/grafana2.png)
![alt text](assets/grafana3.png)
![alt text](assets/grafana4.png)
![alt text](assets/grafana5.png)
![alt text](assets/grafana6.png)
![alt text](assets/grafana7.png)
![alt text](assets/grafana8.png)
![alt text](assets/grafana9.png)
![alt text](assets/grafana10.png)
![alt text](assets/grafana11.png)
![alt text](assets/grafana12.png)
![alt text](assets/grafana13.png)
![alt text](assets/grafana14.png)
![alt text](assets/grafana15.png)

![alt text](assets/eks.png)
![alt text](assets/nodes.png)
![alt text](assets/route53.png)
![alt text](assets/acm1.png)
![alt text](assets/acm2.png)
![alt text](assets/acm3.png)

## Architectural Diagram
Below is a simple diagram of the architectural layout of the entire set up:

![alt text](assets/architecture.drawio.png)

