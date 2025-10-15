# 📚 Bitcoin, La première des Blockchains 🚀


## 1️⃣ **Histoire de Bitcoin** 📜

Bitcoin a été introduit en **2008** par une personne ou un groupe sous le pseudonyme **Satoshi Nakamoto** dans un livre blanc intitulé *Bitcoin: A Peer-to-Peer Electronic Cash System*. Voici les jalons clés :

- **2008** : Publication du livre blanc décrivant un système de paiement décentralisé sans intermédiaire.
- **3 janvier 2009** : Création du **bloc genesis**, le premier bloc de la blockchain Bitcoin.
- **2010** : Première transaction réelle (10 000 BTC pour 2 pizzas 🍕).
- **2017** : Pic de popularité et adoption croissante, malgré des débats sur la scalabilité (SegWit, Bitcoin Cash).
- **2021** : Bitcoin atteint un sommet historique à ~69 000 $ et devient un actif reconnu mondialement.

**Objectif de Bitcoin** : Offrir une monnaie numérique décentralisée, résistante à la censure, et sans besoin d'intermédiaires comme les banques. 🏦❌

---

## 2️⃣ **Structure d’un Bloc** 🧱

Un bloc est l’unité de base de la blockchain Bitcoin. Chaque bloc contient :

- **En-tête du bloc** :
  - **Version** : Version du protocole Bitcoin.
  - **Hash du bloc précédent** : Lien avec le bloc antérieur, assurant l’immuabilité.
  - **Racine de Merkle** : Résumé cryptographique des transactions du bloc.
  - **Horodatage** : Date et heure de création.
  - **Difficulté cible** : Niveau de difficulté pour le minage.
  - **Nonce** : Nombre utilisé pour résoudre le puzzle du Proof of Work.
- **Liste des transactions** : Ensemble des transactions validées incluses dans le bloc.

**Taille moyenne d’un bloc** : ~1 Mo (limité pour contrôler la taille de la blockchain). 📏

---

## 3️⃣ **Modèle UTXO** 💸

Le modèle **UTXO** (Unspent Transaction Output) est au cœur du système de Bitcoin pour gérer les soldes.

- **Qu’est-ce qu’un UTXO ?** : Un UTXO représente une somme d’argent non dépensée issue d’une transaction précédente. Chaque portefeuille contient un ensemble d’UTXOs.
- **Fonctionnement** :
  1. Une transaction consomme des UTXOs comme **entrées** (inputs).
  2. Elle génère de nouveaux UTXOs comme **sorties** (outputs).
  3. Les UTXOs sont verrouillés par des clés publiques et déverrouillés par des signatures.
- **Avantage** : Simplicité et transparence, car chaque UTXO est traçable dans la blockchain.

Exemple : Si Alice envoie 1 BTC à Bob, elle utilise un UTXO de 1,5 BTC, envoie 1 BTC à Bob (nouvel UTXO) et 0,5 BTC à elle-même (UTXO de change). 🔄

---

## 4️⃣ **Signatures et ECDSA** 🔒

Bitcoin utilise **ECDSA** (Elliptic Curve Digital Signature Algorithm) pour sécuriser les transactions.

- **Clé privée/publique** :
  - Une **clé privée** est un secret permettant de signer une transaction.
  - Une **clé publique** est dérivée de la clé privée et sert à vérifier la signature.
- **Signature** :
  - Lors d’une transaction, l’expéditeur signe avec sa clé privée pour prouver qu’il est autorisé à dépenser un UTXO.
  - Les nœuds vérifient la signature à l’aide de la clé publique.
- **ECDSA** : Basé sur les courbes elliptiques, il offre une sécurité élevée avec des clés courtes. 🔐

**Avantage** : Garantit l’intégrité et l’authenticité des transactions sans révéler la clé privée.

---

## 5️⃣ **Sécurité de Bitcoin** 🛡️

La sécurité de Bitcoin repose sur plusieurs piliers :

- **Décentralisation** : Aucun point de contrôle unique, grâce à des milliers de nœuds.
- **Cryptographie** : Utilisation de hachage (SHA-256) et de signatures ECDSA.
- **Immuabilité** : Une fois validé, un bloc est extrêmement difficile à modifier (attaque 51 % coûteuse).
- **Consensus** : Les nœuds doivent s’accorder sur l’état de la blockchain via le Proof of Work.

**Menaces potentielles** :
- Attaque des 51 % : Un acteur malveillant contrôle plus de 50 % de la puissance de calcul (rare et coûteux).
- Vulnérabilités logicielles : Bugs dans le code (corrigés par la communauté). 🐛

---

## 6️⃣ **Hachage et Racine de Merkle** 🔍

### Hachage (SHA-256) 🧮
- **Définition** : Une fonction de hachage (SHA-256) transforme une donnée en une empreinte unique de 256 bits.
- **Propriétés** :
  - **Déterministe** : Même entrée = même sortie.
  - **Résistance à la collision** : Difficile de trouver deux entrées produisant le même hachage.
  - **Irreversibilité** : Impossible de retrouver l’entrée à partir du hachage.
- **Utilisation** : Sécuriser les blocs, lier les blocs (hash du bloc précédent), et générer des adresses.

### Racine de Merkle 🌳
- **Définition** : Structure arborescente qui résume toutes les transactions d’un bloc en un seul hachage.
- **Fonctionnement** :
  1. Chaque transaction est hachée.
  2. Les hachages sont regroupés par paires et hachés à nouveau.
  3. Le processus se répète jusqu’à obtenir un seul hachage : la **racine de Merkle**.
- **Avantage** : Permet de vérifier l’intégrité et la présence d’une transaction dans un bloc efficacement.

---

## 7️⃣ **Minage et Proof of Work (PoW)** ⛏️

### Minage
- **Rôle** : Les mineurs valident les transactions et créent de nouveaux blocs.
- **Processus** :
  1. Collecter les transactions en attente.
  2. Vérifier leur validité.
  3. Résoudre un puzzle cryptographique (PoW) en ajustant le **nonce**.
  4. Ajouter le bloc à la blockchain et recevoir une récompense (BTC + frais de transaction).

### Proof of Work (PoW)
- **Concept** : Les mineurs doivent trouver un nonce tel que le hachage de l’en-tête du bloc soit inférieur à la **cible de difficulté**.
- **Équation** : `SHA-256(en-tête) < cible`
- **Ressources** : Nécessite une puissance de calcul importante (ASICs). ⚡️

**Récompense** : Initialement 50 BTC par bloc (2009), réduite de moitié tous les ~4 ans (halving). En 2025, ~3,125 BTC par bloc.

---

## 8️⃣ **Difficulté et Cible** 🎯

- **Difficulté** : Mesure de la complexité pour résoudre le puzzle PoW.
- **Cible** : Valeur numérique que le hachage du bloc doit être inférieur pour être valide.
- **Ajustement** : Tous les 2016 blocs (~2 semaines), la difficulté est recalculée pour maintenir un temps moyen de 10 minutes par bloc.
- **Formule** : `Difficulté = Difficulté_max / Cible`
- **Impact** : Plus la puissance de calcul globale augmente, plus la difficulté croît.

---

## 9️⃣ **Rôle des Nœuds** 🌐

Les **nœuds** sont les ordinateurs qui maintiennent la blockchain. Ils ont plusieurs rôles :

- **Nœuds complets** : Stockent une copie complète de la blockchain et valident les transactions/blocs.
- **Nœuds légers** : Ne stockent que les en-têtes des blocs (SPV, Simplified Payment Verification).
- **Mineurs** : Un type de nœud qui participe au minage.
- **Validation** : Vérifient que les transactions respectent les règles (pas de double dépense, signatures valides).

**Importance** : Les nœuds assurent la décentralisation et la résilience du réseau. 🕸️

---

## 🔟 **Fonctionnement d’une Transaction** 💳

1. **Initiation** : Alice veut envoyer 1 BTC à Bob. Elle crée une transaction avec :
   - **Entrées** : UTXOs qu’elle possède.
   - **Sorties** : Adresse de Bob (1 BTC) et adresse de change (si nécessaire).
   - **Signature** : Alice signe avec sa clé privée.
2. **Propagation** : La transaction est envoyée au réseau et placée dans le **mempool** (transactions en attente).
3. **Validation** : Les nœuds vérifient la validité (signatures, pas de double dépense).
4. **Inclusion dans un bloc** : Un mineur inclut la transaction dans un bloc.
5. **Confirmation** : Une fois le bloc miné et ajouté à la blockchain, la transaction est confirmée.

**Frais de transaction** : Payés aux mineurs pour prioriser une transaction. 💸

---

## 1️⃣1️⃣ **Validation d’une Transaction** ✅

Pour qu’une transaction soit validée, les nœuds vérifient :

- **Signatures valides** : La signature ECDSA correspond à la clé publique.
- **UTXOs non dépensés** : Les entrées n’ont pas été utilisées ailleurs.
- **Somme des entrées ≥ somme des sorties** : Pas de création de BTC frauduleuse.
- **Règles du protocole** : Format correct, taille, etc.

Une fois validée, la transaction est propagée et peut être incluse dans un bloc. 🛠️

---

