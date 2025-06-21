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
