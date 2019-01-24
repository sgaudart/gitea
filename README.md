# GITEA

https://github.com/go-gitea/gitea/

## Install

### git

Il faut installer le package `git` sur le serveur.

### Database

Créer une database+user coté MySQL/Mariadb (+install si inexistant)


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

Télécharge le package gitea



## Problèmes connus

>Comment uploader des fichiers de plus de 3 Mo ?

Solution : voir fichier de `conf/app.ini` (section repository)
