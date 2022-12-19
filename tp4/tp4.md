
# TP4 : Conteneurs

## I. Docker

### 1. Install

-> installation de `yum`
```
[ynce@dockers1 ~]$ sudo dnf install -y yum-utils
[...]
Installing:
 yum-utils         noarch         4.0.24-4.el9_0           baseos          36 k
[...]
Complete!
```

-> configuration du référentiel
```
[ynce@dockers1 ~]$ sudo yum-config-manager \
> --add-repo \
> https://download.docker.com/linux/centos/docker-ce.repo
Adding repo from: https://download.docker.com/linux/centos/docker-ce.repo
```

-> installation de Docker
```
[ynce@dockers1 ~]$ sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
[...]
Installing:
 containerd.io                x86_64 1.6.10-3.1.el9      docker-ce-stable  32 M
 docker-ce                    x86_64 3:20.10.21-3.el9    docker-ce-stable  21 M
 docker-ce-cli                x86_64 1:20.10.21-3.el9    docker-ce-stable  29 M
 docker-compose-plugin        x86_64 2.12.2-3.el9        docker-ce-stable  10 M
[...]
Complete!
```

-> démarrage du service
```
[ynce@dockers1 ~]$ sudo systemctl start docker
[ynce@dockers1 ~]$ sudo systemctl enable docker
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /usr/lib/systemd/system/docker.service.
[ynce@dockers1 ~]$ sudo systemctl status docker
● docker.service - Docker Application Container Engine
     Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; vendor pr>
     Active: active (running) since Thu 2022-11-24 11:20:48 CET; 22s ago
TriggeredBy: ● docker.socket
[...]
```

-> ajout de l'utilisateur dans le groupe `docker`
```
[ynce@dockers1 ~]$ sudo gpasswd -a ynce docker
Adding user ynce to group docker
```

-> redémarrage de la machine
```
[ynce@dockers1 ~]$ sudo reboot
```

### 3. Lancement de conteneurs

-> utilisation de la commande `docker run`
```
[ynce@dockers1 ~]$ docker run --name base1 -d -v /home/ynce/conf:/etc/nginx/conf.d -v /home/ynce/html/:/usr/share/nginx/html -m 500mb --cpus 0.50 -p 9999:80 nginx
66edcd2282a67b9e1a2aa330564f524b8184bf99b2687ca0fff716dcf3e1bbc3
```

-> vérification
```
[ynce@dockers1 ~]$ curl 172.17.0.2:9999
<!DOCTYPE html>
<html lang="en">
[...]
<body>
	<div id="main">
		<h1>Home page</h1>
	</div>
</body>
</html>
```
