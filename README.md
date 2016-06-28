# MapR
MapR Installation in GCP

### Logiciels déja installé dans GCP 

> Python 2.6
> 

1. Prerequis 

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
$ 
```

> Installation Gcloud

```sh
$ curl https://sdk.cloud.google.com | bash
$ exec -l $SHELL
$ gcloud components list # Afficher toutes les composantes de gcloud
```

> Installation Java 8

```sh
$ 
```





