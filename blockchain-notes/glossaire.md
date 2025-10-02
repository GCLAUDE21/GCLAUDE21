# 📘 Glossaire Blockchain

Un aperçu des notions essentielles pour comprendre le fonctionnement du Bitcoin et de la blockchain en général.

---

## 🌍 Concepts généraux

- 🪙 **Bitcoin**  
  Lancé en 2009 par Satoshi Nakamoto, Bitcoin est la première cryptomonnaie en termes de capitalisation.  
  C’est une **base de données et un logiciel** partagé entre plusieurs ordinateurs appelés **nœuds**.  
  Ceux-ci communiquent entre eux en pair-à-pair, sans entité centralisée.

- 📄 **White Paper**  
  Document qui décrit le fonctionnement d’un projet.  
  Exemple : *Bitcoin – A Peer-to-Peer Electronic Cash System*.

- 📖 **Registre**  
  Base de données regroupant l’historique de toutes les transactions Bitcoin depuis sa création.  
  Chaque nouveau bloc s’ajoute à cette chaîne : **la blockchain**.  
  Une fois inscrite, une transaction devient immuable.

- ⏳ **Mempool**  
  Ensemble des transactions reçues par un nœud en attente d’être ajoutées à un bloc.

- 🧱 **Bloc**  
  Chaque bloc contient :  
  - le **hash** du bloc précédent  
  - la **racine de Merkle**  
  - le **timestamp** (time)  
  - la **difficulté**  
  - le **nonce**  
  - la **liste des transactions**

- 🌲 **Racine de Merkle**  
  Empreinte numérique obtenue par hachage successif des transactions, deux par deux, formant un **arbre de Merkle**.  
  La racine résume toutes les transactions du bloc.

- ⏰ **Time (Timestamp)**  
  Heure de minage du bloc, exprimée en secondes depuis le 1er janvier 1970 (Unix epoch).

- 🎯 **Difficulté / Cible**  
  Nombre en 32 bits servant de seuil pour la preuve de travail.  
  Plus la cible est basse, plus la preuve de travail est difficile à trouver.

- 🔢 **Nonce**  
  Nombre en 32 bits que les mineurs doivent ajuster pour que la hash du bloc soit valide en fonction de la cible.

- 🔑 **Clé privée**  
  Nombre aléatoire de 256 bits (souvent représenté en hexadécimal).  
  Elle permet de signer les transactions.  
  Peut être convertie en une suite de mots appelée **Mnemonic Seed**.

- 🔓 **Clé publique**  
  Dérivée de la clé privée via une fonction mathématique de courbe elliptique.  
  Elle permet de :  
  - vérifier l’auteur d’une transaction  
  - recevoir des fonds  
  ⚠️ Impossible de retrouver la clé privée à partir de la clé publique.

---

## 🔄 Transactions

- 💵 **UTXO (Unspent Transaction Output)**  
  Modèle utilisé par Bitcoin pour représenter les soldes.  
  Chaque transaction détruit les anciens UTXO et crée de nouveaux UTXO, verrouillés par un script (**ScriptPubKey**) contenant l’adresse et la condition de dépense.

- ✍️ **Signature digitale**  
  Permet de signer une transaction sans révéler la clé privée.  
  Elle prouve que l’émetteur détient bien la clé privée associée à la clé publique.  
  Bitcoin utilise la cryptographie par courbes elliptiques (**ECDSA**).

- ⏱ **Locktime**  
  Paramètre facultatif d’une transaction qui bloque l’utilisation d’UTXO jusqu’à un certain temps.

- 📉 **Taux de purge**  
  Indicateur des frais minimums à appliquer pour éviter qu’une transaction soit rejetée par les mempools des nœuds.

---

## ⛏️ Minage & Consensus
