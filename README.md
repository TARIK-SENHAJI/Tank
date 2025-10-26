# Entraînement d'un modèle YOLOv12 pour la détection de véhicules militaires 

Ce projet contient un pipeline complet pour l'entraînement (fine-tuning) d'un modèle de détection d'objets YOLOv12.

## Aperçu du processus

Le notebook (`train.ipynb`) exécute les étapes suivantes :

* **Configuration de l'environnement :** Installation des bibliothèques nécessaires, y compris `roboflow`, `supervision`, `flash-attn`, et le modèle YOLOv12 depuis son dépôt GitHub.
* **Vérification du GPU :** S'assure qu'un GPU NVIDIA compatible (architecture Ampere ou plus récente pour FlashAttention) est disponible.
* **Acquisition des données :** Téléchargement du jeu de données personnalisé "classavehicle" depuis Roboflow au format YOLOv12.
* **Préparation des données :** Modification du fichier `data.yaml` pour garantir que les chemins d'accès aux ensembles d'entraînement, de validation et de test sont corrects.
* **Entraînement du modèle :** Fine-tuning d'un modèle `yolov12s` sur les données personnalisées pendant 100 époques.
* **Évaluation :** Évaluation des performances du modèle entraîné à l'aide de matrices de confusion, de graphiques de résultats et du calcul des métriques Mean Average Precision (mAP).
* **Inférence :** Chargement des meilleurs poids (`best.pt`) pour exécuter des prédictions sur des images aléatoires du jeu de test et visualiser les résultats.

## Performances et Résultats

L'entraînement a été exécuté pendant 100 époques. Les performances finales du modèle sur l'ensemble de validation sont les suivantes :

| Métrique | Score |
| :--- | :--- |
| **mAP50-95(B)** | 0.653 |
| **mAP50(B)** | 0.935 |

Les logs complets de l'entraînement sont disponibles dans `results.csv`.

## Comment l'utiliser

### 1. Prérequis

Assurez-vous d'avoir un environnement avec un GPU NVIDIA (recommandé sur Google Colab).

### 2. Installation

Les dépendances principales peuvent être installées via `pip` :

```bash
!pip install roboflow
!pip install -q git+[https://github.com/sunsmarterjie/yolov12.git](https://github.com/sunsmarterjie/yolov12.git) roboflow supervision flash-attn
