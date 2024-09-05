# Guide d'Installation et d'Exécution du Projet de Suivi d'Objets avec YOLOv4-tiny

## 1. Création d'un Environnement Virtuel

1. Assurez-vous d'avoir Anaconda ou Miniconda installé.
2. Créez un environnement virtuel avec Python 3.8.19 :
    ```bash
    conda create --name [nom_de_l'environnement] python=3.8
    ```
   Remplacez `[nom_de_l'environnement]` par le nom que vous souhaitez donner à votre environnement.

## 2. Installation des Dépendances

1. Activez l'environnement virtuel :
    ```bash
    conda activate [nom_de_l'environnement]
    ```
2. Installez les packages requis en utilisant le fichier `requirements.txt` :
    ```bash
    pip install -r requirements.txt
    ```

## 3. Sauvegarde du Modèle Pré-entrainé YOLOv4-tiny

1. Téléchargez et convertissez le modèle pré-entraîné YOLOv4-tiny pour TensorFlow :
    ```bash
    python save_model.py --weights ./data/yolov4-tiny.weights --output ./checkpoints/yolov4-tiny-416 --model yolov4 --tiny
    ```
   - Le modèle sera sauvegardé dans le dossier `checkpoints` sous le nom `yolov4-tiny-416`.

## 4. Exécution du Script Principal `ObjectTracker.py`

1. Pour exécuter le suivi d'objets sur une vidéo :
    ```bash
    python object_tracker.py --weights ./checkpoints/yolov4-tiny-416 --model yolov4 --video ./data/video/test.mp4 --output ./outputs/tiny.avi --tiny
    ```
   - **`--weights`** : Chemin vers le modèle YOLOv4-tiny sauvegardé.
   - **`--model`** : Modèle à utiliser (`yolov4`).
   - **`--video`** : Chemin vers la vidéo d'entrée.
   - **`--output`** : Chemin où la vidéo traitée sera sauvegardée.
   - **`--tiny`** : Spécifie que vous utilisez la version YOLOv4-tiny.

2. Pour utiliser la webcam à la place d'une vidéo :
    ```bash
    python object_tracker.py --weights ./checkpoints/yolov4-tiny-416 --model yolov4 --video 0 --output ./outputs/tiny.avi --tiny
    ```
   - Remplacez le chemin de la vidéo d'entrée par `0` pour activer la webcam.

---

**Note :** Assurez-vous que toutes les commandes soient exécutées dans l'environnement virtuel activé.

