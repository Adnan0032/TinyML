# 🚀 Drone Detection with Raspberry Pi 4 & ReSpeaker

Ce projet implémente un système de détection de drones à l'aide d'un modèle d'intelligence artificielle embarqué sur un **Raspberry Pi 4**. Il utilise un **ReSpeaker** pour l'acquisition audio et un modèle **TensorFlow Lite (TFLite)** pour la classification en temps réel.

## 🧠 Implémentation du Modèle AI

1. **Acquisition et Prétraitement des Données**
   - Un dataset contenant des audios de drones et d'autres bruits a été collecté.
   - Chaque enregistrement est découpé en segments de **2047 samples** (environ 0.125s à 16kHz).
   - Le signal brut est normalisé avant d’être utilisé pour l'entraînement.

2. **Entraînement du Modèle**
   - Un modèle **CNN** a été entraîné sur ces données pour classer **drone vs. non-drone**.
   - Le modèle a été converti en **TensorFlow Lite (TFLite)** pour une exécution optimisée sur Raspberry Pi.

3. **Intégration dans le Raspberry Pi**
   - Un script capte le son via le **ReSpeaker**, le découpe en segments d'1 seconde et l'enregistre.
   - Un second script charge ces segments, les normalise et les envoie au modèle TFLite.
   - Les résultats de classification s'affichent en temps réel.

---

## 📦 Installation

### 1️⃣ Configurer le Raspberry Pi 4
Assurez-vous que votre Raspberry Pi est à jour :

