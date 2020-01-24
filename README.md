# GITEA

https://github.com/go-gitea/gitea/

## Install

### git

Il faut installer le package `git` sur le serveur.

### Database

Installer MySQL/MariaDB si nécessaire.

Créer une database :
```
CREATE DATABASE gitea CHARACTER SET utf8 COLLATE utf8_general_ci;
```

Créer un user coté Mariadb
```
CREATE USER 'gitea'@'localhost' IDENTIFIED BY 'motdepasse';
GRANT ALL PRIVILEGES ON gitea.* TO 'gitea'@'localhost' IDENTIFIED BY 'motdepasse' WITH GRANT OPTION;
```

### User Git

Créer un user gitea :
`adduser --system --shell /bin/bash --comment 'Gitea user' --user-group  --home-dir /home/git git`

### Create directories

Creation des répertoires :
```
sudo mkdir -p /home/git/gitea/{custom,data,indexers,public,log}
sudo chown git:git /home/git/gitea/{custom,data,indexers,public,log}
sudo chmod 750 /home/git/gitea/{custom,data,indexers,public,log}
sudo chown git:git /home/git/gitea
```

### Download binary

Télécharger le package gitea :
```
cd /home/git/gitea
sudo wget -O gitea https://dl.gitea.io/gitea/VERSION/gitea-VERSION-linux-amd64
sudo mv gitea* gitea
sudo chmod +x gitea
```

### Install web setup

http://YOUR_SERVER_IP:3000/install

## Problèmes connus

>Comment uploader des fichiers de plus de 3 Mo ?

Solution : voir fichier de `conf/app.ini` (section repository) et mettre la section suivante :
```
[repository.upload]
ENABLED = true
FILE_MAX_SIZE = 30
MAX_FILES = 5
```
