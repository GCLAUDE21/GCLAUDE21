# 📘 Glossaire Blockchain

Un aperçu des notions essentielles pour comprendre le fonctionnement du Bitcoin et de la blockchain en général.

---

## 🌍 Concepts généraux

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

# ⛏️ Minage & Consensus


![Bitcoin](https://img.shields.io/badge/Bitcoin-ffd43b?style=for-the-badge&logo=bitcoin&logoColor=000000) 
![Proof of Work](https://img.shields.io/badge/Consensus-Proof%20of%20Work-999?style=for-the-badge) 
![SHA-256](https://img.shields.io/badge/Algorithme-SHA--256-4b8bbe?style=for-the-badge)


Cette section présente les notions clés liées au **minage** et aux **mécanismes de consensus** (Proof of Work / PoW).  
Le style est technique et synthétique — idéal pour documenter une formation ou un dossier technique.

---

### 🔢 Hashrate

Le **hashrate** est la quantité de calculs (hashes) réalisés par unité de temps par les mineurs — généralement mesurée en H/s, kH/s, MH/s, GH/s, TH/s, etc.  
Il reflète la puissance de calcul disponible pour sécuriser la blockchain et trouver des blocs valides.

**Importance :** un hashrate élevé augmente la sécurité du réseau (rendant une attaque coûteuse) et diminue la probabilité pour un seul mineur ou pool de contrôler la chaîne.

---

### ✂️ Halving

Le **halving** (ou réduction de moitié) est l’événement programmé où la récompense de minage par bloc est réduite de **50%**.  
Cela se produit tous les ~210 000 blocs pour Bitcoin (environ tous les 4 ans).

**Effet :** diminue l'émission monétaire, influant potentiellement sur l’offre et le prix si la demande reste constante.

---

### 🧾 Coinbase (transaction de coinbase)

La **transaction coinbase** est la première transaction d’un bloc.  
Elle crée la récompense du bloc (nouvelles pièces + frais de transaction) et la crédite à l’adresse du mineur.

Pour Bitcoin, les sorties de coinbase sont soumises à une période de **maturation de 100 blocs** avant de pouvoir être dépensées.

---

### 🤝 Pools de minage

Un **pool de minage** regroupe la puissance de calcul de plusieurs mineurs pour rechercher ensemble le même bloc.  
Les récompenses sont ensuite partagées proportionnellement entre les contributeurs selon les règles du pool.

**Pourquoi ?**
- Lisse la variance des paiements (paiements plus réguliers pour les petits mineurs).
- Réduit le hasard de trouver un bloc seul.
- Peut néanmoins augmenter la centralisation si un pool devient trop grand.

---

### ⚠️ Attaque à 51% (Majority Attack)

Si une entité (ou coalition) contrôle **≥ 51%** du hashrate du réseau, elle peut :

- **Réorganiser** la blockchain (forks privés).
- **Censurer** certaines transactions.
- **Réaliser des doubles dépenses** en réécrivant l’historique des blocs qu’elle contrôle.

**Contraintes pratiques :**
- Maintenir un contrôle ≥ 51% est extrêmement coûteux (matériel + électricité).
- Pour réussir une double dépense, l’attaquant doit contrôler le réseau pendant plusieurs blocs consécutifs.  
  (Les commerçants exigent souvent **6 confirmations** comme seuil de sécurité empirique.)



