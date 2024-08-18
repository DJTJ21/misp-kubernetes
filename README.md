# MISP Kubernetes Deployment

## Description

Ce dépôt contient les configurations nécessaires pour déployer MISP (Malware Information Sharing Platform) sur un cluster Kubernetes. MISP est une plateforme de partage d'informations sur les menaces de cybersécurité. L'objectif de ce projet est de fournir une configuration prête à l'emploi pour exécuter MISP dans un environnement Kubernetes, en utilisant des ressources telles que des déploiements, des services, et des volumes persistants.

## Contenu du Dépôt

- **`misp-kubernetes/`** : Contient les fichiers de configuration Kubernetes pour déployer MISP.
 - **`misp-deployment.yaml`** : Définition du déploiement Kubernetes pour MISP.
 - **`misp-service.yaml`** : Configuration du service Kubernetes pour exposer MISP.
 - **`misp-configmap.yaml`** : ConfigMap pour les variables d'environnement et configurations spécifiques à MISP.
 - **`misp-pvc.yaml`** : PersistentVolumeClaim pour le stockage persistant des données de MISP.

## Prérequis

- Kubernetes 1.18 ou version ultérieure
- `kubectl` installé et configuré pour interagir avec votre cluster Kubernetes

## Installation

1. **Cloner le dépôt :**

   ```bash
   git clone https://github.com/DJTJ21/misp-kubernetes.git
   cd misp-kubernetes
   ```

2.  **Déployer MISP sur Kubernetes :**
    
    -   Créez les PersistentVolumeClaims (PVC) :
        
  
        `kubectl apply -f kubernetes/misp-pvc.yaml` 
        
    -   Déployez les configurations MISP :
        
       ```bash
        kubectl apply -f kubernetes/misp-configmap.yaml
        kubectl apply -f kubernetes/misp-deployment.yaml
        kubectl apply -f kubernetes/misp-service.yaml
       ```
3.  **Accéder à MISP :**
    
    -   Une fois le déploiement terminé, vous pouvez accéder à l'interface web de MISP via le service Kubernetes. Utilisez la commande suivante pour obtenir l'adresse IP ou le nom de domaine externe (si un LoadBalancer est utilisé) :
        
    ```bash
    kubectl get svc misp-service
    ```
## Utilisation

Après le déploiement, vous pouvez accéder à MISP à l'adresse IP ou au nom de domaine fourni par le service Kubernetes. Assurez-vous de configurer correctement les variables d'environnement et les secrets nécessaires pour que MISP fonctionne correctement.
