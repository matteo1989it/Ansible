This exercice tries to provide one possible way to set up the Continuous Integration, Delivery or Deployment pipeline. We'll use Jenkins, Docker, Ansible. Two servers will be needed. One will be used as a Jenkins server and the other one as an imitation of production servers. First one will checkout, test and build applications while perform deployment and post-deployment tests.

You'll need Git installed. The rest of the tools will be set up as part of the exercises in this article.

CI/CD Environment
We'll set up Jenkins environment using Ansible. Create a VM with Ubuntu (use your VirtualBox VM or CloudVM) and run the bootstrap.sh script. The only purpose of that script is to install Ansible. Once that is done, Ansible will make sure that Docker is installed and Jenkins process is running.

Install Vagrant :
https://www.vagrantup.com/downloads.html

Execute Vragrant script :
If you run into issues with Ansible complaining about executable permissions, try modifying the Vagrantfile's synced_folder entry from config.vm.synced_folder ".", "/vagrant" to
config.vm.synced_folder ".", "/vagrant", mount_options: ["dmode=700,fmode=600"]. You'll find an example in the

To Deploy both vms (cd and prod) :
* vagrant up cd
* vagrant up prod

To Access inside both Vms :
* vagrant ssh cd
* vagrant ssh prod


Exercice Objectives :
* **Step 1 - CI/CD Environment** : Auto Installation of Jenkins in a Virtual Machine (not a docker container). 
* **Step 2 - CI/CD Environment** : Interconnect services : Jenkins, Github, Sonar, Nexus, Maven. Write the scripts in Jenkins for it to order Ansible to AutoDeploy. 
* **Step 3 - Application Deployment** : Using Ansible and Docker (2 webservers, 1 Database server, 1 Front HA), deploy a provided webapp available through a Github repository.

