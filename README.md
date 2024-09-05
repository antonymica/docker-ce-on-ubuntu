# TUTOUS

<h1>Installation de Docker CE sur Ubuntu 22.04</h1> 

Ce guide vous explique comment installer Docker CE (Community Edition) sur une machine Ubuntu 22.04.

## Prérequis

- Un système Ubuntu 22.04 installé.
- Un utilisateur avec des privilèges sudo.

## Étapes d'installation

Pour installer Docker CE, exécutez les commandes suivantes dans l'ordre :


# 1. Mettre à jour le système
```bash
sudo apt update
sudo apt upgrade -y
```

# 2. Installer les paquets nécessaires
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

# 3. Ajouter la clé GPG officielle de Docker

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

# 4. Ajouter le dépôt Docker

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

# 5. Installer Docker CE

```bash
sudo apt update
sudo apt install docker-ce -y
```

# 6. Vérifier l'installation

```bash
sudo docker --version
```

# 7. (Optionnel) Ajouter votre utilisateur au groupe Docker pour exécuter Docker sans sudo

```bash
sudo usermod -aG docker $USER
su - ${USER}
groups
sudo usermod -aG docker username
```

# 8. Démarrer et activer Docker
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

# 9. Tester Docker
```bash
docker run hello-world
```


