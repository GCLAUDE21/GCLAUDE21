# ₿ Bitcoin — La première des Blockchains

## ⚙️ Introduction

Bitcoin est le premier réseau **blockchain public décentralisé**.  
Son objectif est simple : Un système de paiement **pair-à-pair**, sans autorité centrale, avec une sécurité garantie par les mathématiques et le consensus.

- **Création :** 2008 (Livre blanc de Satoshi Nakamoto)  
- **Lancement :** 2009  
- **Fonctionnement :** Blockchain + preuve de travail (Proof of Work)

---

## 🧱 1. Structure des Transactions — UTXO

Bitcoin repose sur un **modèle UTXO (Unspent Transaction Output)**, semblable au cash, différent des comptes classiques (comme Ethereum).

### 🔹 Principe :
Chaque transaction consomme des *UTXO* existants (outputs non dépensés) et crée de nouveaux *UTXO*.

Chaque sortie est verrouillée par une **clé publique**.  
Pour dépenser ces fonds, il faut **la signature correspondant à la clé privée**.

### 💡 Exemple :

➡️ Alice dépense 1 BTC (UTXO)  
➡️ Création de **2 nouveaux UTXO** :
- 0.7 BTC → Bob  
- 0.3 BTC → Alice (nouvelle adresse)

### 🧩 Avantage :
- Transactions **traçables, divisibles, indépendantes**
- Aucune balance globale : seules les sorties non dépensées comptent

---

## 🔒 2. Cryptographie et Signatures

Chaque utilisateur détient :
- Une **clé privée** → signature numérique (preuve de propriété)
- Une **clé publique** → identifiant visible sur le réseau


🧠 **Hash + signature = intégrité + authenticité**

---

## ⛏️ 3. Le Minage (Proof of Work)

### 🔹 Objectif :
Sécuriser le réseau et ajouter de nouveaux blocs à la blockchain.

Les mineurs :
1. Sélectionnent les transactions, avec le plus de frais, valides du mempool  
2. Les regroupent dans un **bloc candidat**  
3. Tentent de résoudre un **problème cryptographique** :  
   trouver un hash inférieur à une cible donnée (`target`)


L'en-tête du bloc contient :
- Hash du bloc précédent
- Racine Merkle (hash des transactions deux à deux)
- Nonce (nombre ajusté pour le minage )
- Timestamp
- Target / Cible

Le but :  
👉 Trouver un *nonce* tel que  
`hash < target`

### ⚡ Exemple de difficulté :
Plus la **target** est basse, plus il est **difficile** de trouver un hash valide.  
La difficulté s’ajuste tous les **2016 blocs (~2 semaines)**.

---

## 💰 4. Récompenses et Halving

Chaque mineur qui découvre un bloc reçoit :
- La **récompense de bloc** (BTC créés)
- Les **frais de transaction** inclus

⚠️ Cette récompense diminue tous les **210 000 blocs (~4 ans)** :  
C’est le **Halving**.

| Année | Récompense par bloc |
|-------|----------------------|
| 2009  | 50 BTC              |
| 2012  | 25 BTC              |
| 2016  | 12.5 BTC            |
| 2020  | 6.25 BTC            |
| 2024  | 3.125 BTC           |

→ Bitcoin atteindra un total de **21 millions de BTC** d’ici 2140 environ.

---

## 🔁 5. Consensus et Sécurité

Le consensus est garanti par la **preuve de travail** :

- Chaque bloc valide référence le **hash du bloc précédent**  
- Une chaîne concurrente doit **refaire toute la preuve de travail** pour être acceptée  
- La chaîne la plus longue (la plus coûteuse à produire) est la **valide** : C'est le consensus de Nakamoto

🧱 “Longest Chain Rule” = Sécurité par le coût énergétique

---

## 🧠 6. Récapitulatif 

[Transaction] → [Mempool] → [Bloc candidat] → [Minage PoW] → [Bloc validé]

🔹 Transactions = UTXO signés  
🔹 PoW = sécurité & immuabilité  
🔹 Halving = rareté programmée  
🔹 UTXO = traçabilité et transparence

---

