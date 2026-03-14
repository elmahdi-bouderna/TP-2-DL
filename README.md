# TP 2 – Réseau de Neurones Convolutif (CNN)

Auteur : EL MAHDI BOUDERNA  
Email : bouderna.elmahdi@gmail.com  

---

## Description

Ce projet correspond au TP 2 de Deep Learning portant sur l'utilisation des réseaux de neurones convolutifs (CNN) pour la classification d’images avec TensorFlow / Keras.

L’objectif de ce TP est de comprendre le fonctionnement d’un CNN et de mettre en pratique les différentes étapes nécessaires pour entraîner un modèle de classification d’images :

- Préparation et chargement des données
- Prétraitement et augmentation des données
- Construction d’un modèle CNN
- Entraînement et évaluation du modèle
- Analyse des performances
- Amélioration de l’architecture
- Adaptation à des images en niveaux de gris

Le projet a été réalisé dans Google Colab en utilisant Python et TensorFlow/Keras.

---

## Objectifs du TP

Les principaux objectifs de ce TP sont :

- Comprendre le principe des réseaux de neurones convolutifs
- Apprendre à utiliser Keras pour la classification d’images
- Analyser l’impact du prétraitement et de l’augmentation de données
- Proposer une architecture CNN améliorée
- Adapter le modèle pour des images en niveaux de gris

---

## Structure du Dataset

Le dataset utilisé est organisé sous la forme suivante :

images/
│
├── train/
│   ├── class1/
│   └── class2/
│
└── test/
    ├── class1/
    └── class2/

Chaque sous-dossier contient les images correspondant à une classe.

Les images sont chargées automatiquement avec :

ImageDataGenerator.flow_from_directory()

---

## Architecture CNN utilisée

L’architecture de base du modèle CNN est composée de :

1. Une couche Convolution (Conv2D)
2. Une fonction d’activation ReLU
3. Une couche MaxPooling
4. Une opération Flatten
5. Une couche Dense
6. Une couche de sortie Softmax

Cette architecture permet d’extraire des caractéristiques visuelles importantes des images avant de réaliser la classification.

---

## Prétraitement des données

Le prétraitement est réalisé avec ImageDataGenerator, qui permet :

- la normalisation des pixels (rescale=1./255)
- l’augmentation de données

Exemple :

train_datagen = ImageDataGenerator(
    rescale=1./255,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True
)

L’augmentation de données permet d’améliorer la capacité de généralisation du modèle.

---

## Expérimentations réalisées

Dans ce TP, plusieurs expériences ont été effectuées.

### 1. Entraînement du modèle CNN de base

Un modèle CNN simple est entraîné pour effectuer la classification des images.

Les performances sont évaluées à l’aide de :
- l’accuracy
- la loss

Les résultats sont visualisés à l’aide de graphiques.

---

### 2. Suppression de l’augmentation de données

Une seconde expérience consiste à supprimer les transformations :

shear_range  
zoom_range  
horizontal_flip  

et garder uniquement :

rescale = 1./255

Cela permet d’observer l’impact de l’augmentation de données sur la performance du modèle.

---

### 3. Proposition d’une nouvelle architecture CNN

Une architecture plus profonde a été proposée, composée de :

- plusieurs couches convolutionnelles
- plusieurs couches de pooling
- une couche Dropout pour limiter le surapprentissage

Cette architecture permet d’extraire des caractéristiques plus complexes.

---

### 4. Classification en niveaux de gris

Le modèle a été adapté pour traiter des images en niveaux de gris.

Les modifications principales sont :

- utilisation de color_mode='grayscale'
- modification de input_shape :

input_shape = (224, 224, 1)

Cela réduit la complexité du modèle mais peut supprimer certaines informations liées aux couleurs.

---

## Résultats

Les résultats sont analysés à l’aide des courbes :

- Accuracy (train / validation)
- Loss (train / validation)

Les courbes permettent d’observer :

- l’apprentissage du modèle
- le risque de surapprentissage
- l’efficacité de l’architecture proposée

Il est normal que les résultats varient légèrement entre plusieurs exécutions à cause :

- de l’initialisation aléatoire des poids
- du mélange des données
- de l’augmentation de données
- des différences entre CPU et GPU

---

## Technologies utilisées

- Python
- TensorFlow
- Keras
- Google Colab
- Matplotlib

---

## Conclusion

Ce TP a permis de mettre en pratique l’utilisation des réseaux de neurones convolutifs pour la classification d’images.

Nous avons étudié :

- la structure d’un CNN
- l’importance du prétraitement des données
- l’impact de l’augmentation de données
- l’amélioration des performances grâce à une architecture plus profonde

Les CNN constituent aujourd’hui l’une des méthodes les plus efficaces pour les tâches de vision par ordinateur.
