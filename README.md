# 🚀 Drone Sound Detection using Raspberry Pi & TFLite  

## 📌 Description  

Ce projet implémente un modèle d'IA pour détecter les drones à partir de fichiers audio en utilisant TensorFlow Lite (TFLite) sur un Raspberry Pi 4.  

Il se compose de deux parties principales :  
- **record_audio.py** : Enregistre l’audio en segments de 1 seconde à l’aide du ReSpeaker et les stocke dans `test_audios/`.  
- **test_model.py** : Charge le modèle TFLite et effectue des prédictions sur les fichiers audio enregistrés.  

---

## 🏗️ Implémentation du Modèle  

### 🔹 1. Collecte et Prétraitement des Données  
- Les enregistrements audio sont collectés à une fréquence d’échantillonnage de **16 kHz** en format **mono**.  
- Les fichiers sont normalisés avant l'entraînement pour améliorer la robustesse du modèle.  

### 🔹 2. Entraînement du Modèle  
- Un modèle de **CNN (Convolutional Neural Network)** a été entraîné sur **2047 échantillons**.  
- L’audio brut est utilisé comme entrée, sans transformation en spectrogramme.  

### 🔹 3. Conversion en TensorFlow Lite  
- Le modèle entraîné est converti en **TFLite** pour être exécuté efficacement sur un Raspberry Pi.  
- Optimisations effectuées : **Quantization** pour réduire la taille et améliorer les performances.  

---

## 📂 Structure du Projet  

```
📂 drone-detection/
 ├── 📂 models/               # Stockage du modèle
 │    └── drone_detection.tflite
 ├── 📂 test_audios/          # Stockage des enregistrements
 ├── record_audio.py          # Script d'enregistrement audio
 ├── test_model.py            # Script de test du modèle
 ├── requirements.txt         # Dépendances Python
 ├── .gitignore               # Fichiers à ignorer
 ├── README.md                # Documentation du projet
```

---

## 🛠️ Installation & Déploiement  

### 📥 1. Cloner le dépôt  
```bash
git clone https://github.com/votre-utilisateur/drone-detection.git
cd drone-detection
```

### 🏗️ 2. Installer les dépendances  
```bash
pip install -r requirements.txt
```

### 🎙️ 3. Configurer le ReSpeaker  
- Vérifier que le ReSpeaker est bien détecté :  
  ```bash
  arecord -l
  ```
- Configurer `record_audio.py` pour utiliser l’index du périphérique audio.  

---

## 🎤 Utilisation  

### 📝 1. Enregistrer un audio  
```bash
python record_audio.py
```
> 🔹 Génère des fichiers `.wav` dans `test_audios/`.  

### 🤖 2. Tester le modèle sur un audio  
```bash
python test_model.py
```
> 🔹 Effectue la prédiction sur les fichiers `.wav` enregistrés.  

---

## 🖥️ Déploiement sur Raspberry Pi 4  

### 📥 1. Transférer le projet sur le Raspberry Pi  
Sur votre PC :  
```bash
scp -r drone-detection pi@<IP_RPI>:~/
```

### 🚀 2. Exécuter le projet  
```bash
cd drone-detection
python test_model.py
```

---

## 🛠️ Problèmes Connus & Améliorations  

- 📌 **Le modèle détecte mal en présence de bruit**  
  - 🛠️ Solution : Ajouter un **filtrage du bruit** avant l'inférence.  
- 📌 **Temps d’inférence trop long**  
  - 🛠️ Solution : Tester une **quantization INT8** pour accélérer le modèle sur le Raspberry Pi.  

---

## 📜 Licence  
📄 Ce projet est sous licence **MIT**.  

---  
  
🚀 *Développé avec passion par Adnane Ammi Douah (https://github.com//Adnan0032/).*
