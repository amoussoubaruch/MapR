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
```

> Installation Gcloud

```sh
$ curl https://sdk.cloud.google.com | bash
$ exec -l $SHELL
$ gcloud components list # Afficher toutes les composantes de gcloud
```

> Installation Java 8

```sh
$ yum install java-1.7.0-openjdk-devel
```

> Créer des comptes d'utilisateurs sur toutes les machines 

> Installer des packages supplémentaires 

```sh
$ yum -y installpython-pycurl nss openssh-clients openssl sshpass wget
```

> Installer des packages supplémentaires  









