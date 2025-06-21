#Kubernetes setup:
#IMPERATIVE_APPROACH:(where everything in command instead of yaml file)

#in CMD run:
    - systeminfo (to check hypervisor is detected or not)

#Install chocolety:(Run in powershell as administrator)

   - Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

#Install kubectl:(in CMD run as administrator)

    - choco install kubernetes-cli

#Ensure the version is up to date
    - kubectl version --client

#in CMD go to user profile:
   - %USERPROFILE%
   - mkdir .kube (create .kube directory)

 (go to .kube folder and create & create text document named as "config")

#INSTALL MINIKUBE:
(in CMD run as administrator)
  - choco install minikube
(take new cmd)
#Start minikube(create virtual machine):
  - minikube start --driver=docker (or, in CMD run as administrator)
  - minikube delete (if there vm before)
  - minikube status (check minikube state)
  - minikube dashboard ( dashboard)

     (SETUP COMPLETE)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Create a Deployment:
 - kubectl create deployment [deployment-name] --image=[image-from-dockerhub]
#To check deployment:
 - kubectl get deployment
#Delete deployment:
  - kubectl delete deployment [deployment-name]
#To check pods:
 - kubectl get pods
# To delete deployment:
 - kubectl delete deployment [deployment-name]
#Exposing pod which is created by deployment:
 - kubectl expose deployment [deployment-name] --type=LoadBalancer --port=8080

#check services:
  - kubectl get services
# Delete service:
  - kubectl delete service [service-name]
# get ip for local machine:
  - minikube service [service-name]
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


#Scaling Pods:

  - kubectl scale deployment/[deployment-name] --replicas=3[how-many-replicas-you-want]

#check pods
  - kubectl get pods

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#updating deployments:
   #Updating dockerhub image:
     - docker build -t [dockerHubUsername/ImageName]:tag .
     - docker push [dockerHubUsername/ImageName]:tag


#set iamge to deployment:
  - kubectl set image deployment/[deployment-name] [current-container-name]=[dockerHubUsername/ImageName]:tag
#view updating status:
  - kubectl rollout status deployment/[deployment-name]

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#Deployment rollback:(If you want to back previous deployment state)
  - kubectl rollout undo deployment/[deployment-name]

#inspect the progress of rollout:
  - kubectl rollout status deployment/[deployment-name]

#Check deployment history:
  - kubectl rollout history deployment/[deployment-name]

#Detailed about deployment history:
  - kubectl rollout history deployment/[deployment-name] --revision=[revision-number]

#Back to any revision:
  - kubectl rollout undo deployment/[deployment-name] --to-revision=[revision-number]

