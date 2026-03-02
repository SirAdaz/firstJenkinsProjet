# Jenkins Docker Setup

Ce projet permet de lancer Jenkins dans un conteneur Docker.

## Prérequis

- Docker
- Docker Compose

## Démarrage

Pour démarrer Jenkins :

```bash
docker-compose up -d
```

## Accès

Une fois Jenkins démarré, accédez à l'interface web via :
- URL : http://localhost:8081

## Récupération du mot de passe initial

Pour obtenir le mot de passe administrateur initial :

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

Ou via PowerShell :

```powershell
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

## Arrêt

Pour arrêter Jenkins :

```bash
docker-compose down
```

Pour arrêter et supprimer les volumes (⚠️ supprime toutes les données) :

```bash
docker-compose down -v
```

## Configuration

- **Port 8080** : Interface web Jenkins
- **Port 50000** : Port pour les agents Jenkins
- **Volume jenkins_home** : Persiste toutes les données Jenkins (jobs, configurations, plugins)

## Notes

- Le socket Docker est monté dans le conteneur pour permettre à Jenkins d'exécuter des commandes Docker (utile pour les pipelines CI/CD)
- Les données sont persistées dans le volume Docker `jenkins_home`
