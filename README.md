# MapR
MapR 5.1 Installation in GCP

### Logiciels déja installé dans GCP 

> Python 2.6
> 

### MapR info

> Chaque utilisateur du cluster doit avoir un compte sur chaque noeud 
>  Do not use RAID
>  Do not use LVM
> Recommandation pour la capacité de stockage : si on dispose de 50Tb de données, tenir compte du facteur de réplication (Si le facteur de réplication est 3 alors prévoir une space de 150Tb plus 150tb *1.25 pour stocker les log, les données mapreduce et les fichiers temporaires ce qui fait 188TB à prévoir) 
> https://github.com/MapRPS/cluster-validation # MapR tools used for pre-install and post-install tests

1. Prerequis pour l'installation de MapR : Paramétrage à réaliser sur chaque noeud 

> Passer en mode root

```sh
$ sudo -i 
```

> Quelques commandes linux 

```sh
$ uname -m                           # Processor type 
$ uname -a                           # alternative commands
$ grep flags /proc/cpuinfo           # Cpu Info file 
$ cat /proc/version                  # Vesrion de linux 
$ cat /etc/*-release                 # Ou cette commande 
$ free -g                            # Display total and available memory in gigabytes 
$ hostname -f                        # Hostname à utiliser dans le config 
$ getent hosts `hostname`            # Return the node's IP address and fully-qualified domain name (FQDN)
$ netstat -anp | grep 9443           # Vérifier si un port est ouvert
$ lsblk                              # Lister les disques dans linux 
$ telnet mapr1.c.mapr-1355.internal 9443 # Vérifier si le port 9443 est ouvert (Notons que mapr1... est le nom avec fdqn du server)
```

> Installation Gcloud

```sh
$ curl https://sdk.cloud.google.com | bash
$ exec -l $SHELL
$ gcloud components list # Afficher toutes les composantes de gcloud
```

> Installation Java 8

```sh
$ yum install java-1.7.0-openjdk-devel  # Java 7
$ yum install java-1.8.0-openjdk        # Java 8
```

> Créer des comptes d'utilisateurs sur toutes les machines 

> Configuration SSH 

1. Set Up Passwordless SSH

> A réaliser sur tous les noeuds 

```sh
$ passwd root                                   # Changer le mot de passe root (Suivre les instructions pour changer le mot de passe)
$ cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak   # Copy the /etc/ssh/sshd_config file to sshd_config.bak 
$ vi /etc/ssh/sshd_config                           # edit the file with this setting (PermitRootLogin yes PasswordAuthentication yes)
$ sshd –t                                           # Save the file, and run this command 
$ service sshd restart                              # Restart the sshd service
```

> Sur le master nome

```sh
$ ssh-keygen                                                               # Generate key RSA 
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@mapr2.c.mapr-1355.internal     # Copy key to node 1 
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@mapr3.c.mapr-1355.internal     # Copy key to node 2
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@mapr4.c.mapr-1355.internal     # Copy key to node 3
```


> Installer des packages supplémentaires 

```sh
$ yum -y installpython-pycurl nss openssh-clients openssl sshpass wget
$ yum install telnet telnet-server -y   # Installer Telnet 
```











