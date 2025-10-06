# 📘 Glossaire Blockchain

Un aperçu des notions essentielles pour comprendre le fonctionnement du Bitcoin et de la blockchain en général.

---

## 🧠 Concepts Généraux
<p align="center">
  <img src="https://img.shields.io/badge/Bloc-0284c7?style=for-the-badge&logo=codesandbox&logoColor=white" />
  <img src="https://img.shields.io/badge/Blockchain-FF8C00?style=for-the-badge&logo=blockchaindotcom&logoColor=white" />
  <img src="https://img.shields.io/badge/Decentralization-00BFA6?style=for-the-badge&logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/Web3-0A66C2?style=for-the-badge&logo=web3dotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/Cryptography-008080?style=for-the-badge&logo=protonmail&logoColor=white" />
  <img src="https://img.shields.io/badge/Distributed%20Ledger-2DD4BF?style=for-the-badge&logo=hyperledger&logoColor=white" />
</p>


- 📄 **White Paper**  
  Document qui décrit le fonctionnement d’un projet.  
  Exemple : *Bitcoin – A Peer-to-Peer Electronic Cash System*.

- 📖 **Registre distribué (Distributed Ledger)**  
  Base de données partagée, synchronisée et répliquée regroupant l’historique de toutes les transactions Bitcoin depuis sa création.  
  Chaque nouveau bloc s’ajoute à cette chaîne : **la blockchain**.  
  Une fois inscrite, une transaction devient immuable.


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

## 💸 Transactions
<p align="center">
  <img src="https://img.shields.io/badge/Transactions-4ade80?style=for-the-badge&logo=bitcoinsv&logoColor=white" />
  <img src="https://img.shields.io/badge/UTXO-16a34a?style=for-the-badge&logo=bitcoin&logoColor=white" />
  <img src="https://img.shields.io/badge/Signatures%20Numériques-2563eb?style=for-the-badge&logo=keybase&logoColor=white" />
  <img src="https://img.shields.io/badge/Adresses-7e22ce?style=for-the-badge&logo=qrcode&logoColor=white" />
  <img src="https://img.shields.io/badge/Frais%20de%20Transaction-f97316?style=for-the-badge&logo=moneygram&logoColor=white" />
  <img src="https://img.shields.io/badge/Mempool-f59e0b?style=for-the-badge&logo=databricks&logoColor=white" />

  <img src="https://img.shields.io/badge/Validation-059669?style=for-the-badge&logo=vercel&logoColor=white" />
</p>

Les **transactions** sont le cœur du fonctionnement d’une blockchain.  
Elles représentent le transfert de valeur ou d’informations entre différentes adresses du réseau.  
Chaque transaction contient des **entrées (inputs)** et **sorties (outputs)**, et doit être **signée numériquement** par le propriétaire des fonds à l’aide de sa clé privée.

Une fois créée, la transaction est diffusée dans le réseau et stockée temporairement dans la **mempool**,  
en attendant d’être **validée** et **intégrée à un bloc** par un mineur.

---

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

- ⏳ **Mempool**  
  Ensemble des transactions reçues par un nœud en attente d’être ajoutées à un bloc.

---

## ⛏️ Minage & Consensus
<p align="center">
  <img src="https://img.shields.io/badge/Bitcoin-ffd43b?style=for-the-badge&logo=bitcoin&logoColor=000000" />
  <img src="https://img.shields.io/badge/Proof%20of%20Work-999?style=for-the-badge&logo=bitcoin&logoColor=white" />
  <img src="https://img.shields.io/badge/SHA--256-4b8bbe?style=for-the-badge&logo=shield&logoColor=white" />
  <img src="https://img.shields.io/badge/Hashrate-0ea5e9?style=for-the-badge&logo=serverfault&logoColor=white" />
  <img src="https://img.shields.io/badge/Halving-f43f5e?style=for-the-badge&logo=timer&logoColor=white" />
  <img src="https://img.shields.io/badge/Coinbase%20Tx-6d28d9?style=for-the-badge&logo=coinbase&logoColor=white" />
  <img src="https://img.shields.io/badge/Pools%20de%20Minage-10b981?style=for-the-badge&logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/Attaque%2051%25-ef4444?style=for-the-badge&logo=alert&logoColor=white" />
</p>

Cette section présente les notions clés liées au **minage** et aux **mécanismes de consensus** (Proof of Work / PoW).  
Le style est technique et synthétique — idéal pour documenter une formation ou un dossier technique.

---

### 🔢 Hashrate

Le **hashrate** est la quantité de calculs (hashes) réalisés par unité de temps par les mineurs — généralement mesurée en H/s, kH/s, MH/s, GH/s, TH/s, etc.  
Il reflète la puissance de calcul disponible pour sécuriser la blockchain et trouver des blocs valides.

**Importance :** un hashrate élevé augmente la sécurité du réseau (rendant une attaque coûteuse) et diminue la probabilité pour un seul mineur ou pool de contrôler la chaîne.


### 🔐 SHA-256

Le **SHA-256** (*Secure Hash Algorithm 256 bits*) est la **fonction de hachage cryptographique** utilisée par Bitcoin pour sécuriser le processus de minage et garantir l’intégrité des blocs.  
Il transforme toute donnée d’entrée en une empreinte unique de **256 bits**, impossible à inverser.  
C’est ce calcul répété des **hashes SHA-256** qui permet aux mineurs de trouver le bon **nonce** et de valider un nouveau bloc.

> ⚙️ Un simple changement d’un caractère dans les données produit un hash totalement différent — assurant l’immutabilité et la sécurité du réseau.


### ✂️ Halving

Le **halving** (ou réduction de moitié) est l’événement programmé où la récompense de minage par bloc est réduite de **50%**.  
Cela se produit tous les ~210 000 blocs pour Bitcoin (environ tous les 4 ans).

**Effet :** diminue l'émission monétaire, influant potentiellement sur l’offre et le prix si la demande reste constante.


### 🧾 Coinbase (transaction de coinbase)

La **transaction coinbase** est la première transaction d’un bloc.  
Elle crée la récompense du bloc (nouvelles pièces + frais de transaction) et la crédite à l’adresse du mineur.

Pour Bitcoin, les sorties de coinbase sont soumises à une période de **maturation de 100 blocs** avant de pouvoir être dépensées.


### 🤝 Pools de minage

Un **pool de minage** regroupe la puissance de calcul de plusieurs mineurs pour rechercher ensemble le même bloc.  
Les récompenses sont ensuite partagées proportionnellement entre les contributeurs selon les règles du pool.

**Pourquoi ?**
- Lisse la variance des paiements (paiements plus réguliers pour les petits mineurs).
- Réduit le hasard de trouver un bloc seul.
- Peut néanmoins augmenter la centralisation si un pool devient trop grand.


### ⚠️ Attaque à 51% (Majority Attack)

Si une entité (ou coalition) contrôle **≥ 51%** du hashrate du réseau, elle peut :

- **Réorganiser** la blockchain (forks privés).
- **Censurer** certaines transactions.
- **Réaliser des doubles dépenses** en réécrivant l’historique des blocs qu’elle contrôle.

**Contraintes pratiques :**
- Maintenir un contrôle ≥ 51% est extrêmement coûteux (matériel + électricité).
- Pour réussir une double dépense, l’attaquant doit contrôler le réseau pendant plusieurs blocs consécutifs.  
  (Les commerçants exigent souvent **6 confirmations** comme seuil de sécurité empirique.)

## 🧱 Structure d’une Blockchain
<p align="center">
  <img src="https://img.shields.io/badge/Bloc-0284c7?style=for-the-badge&logo=codesandbox&logoColor=white" />
  <img src="https://img.shields.io/badge/Merkle%20Tree-7c3aed?style=for-the-badge&logo=tree&logoColor=white" />
  <img src="https://img.shields.io/badge/Nœuds-059669?style=for-the-badge&logo=serverfault&logoColor=white" />
  <img src="https://img.shields.io/badge/Synchronisation-f97316?style=for-the-badge&logo=sync&logoColor=white" />
</p>

---

## 🪙 Tokens & Cryptomonnaies
<p align="center">
  <img src="https://img.shields.io/badge/Coin-FFD43B?style=for-the-badge&logo=bitcoin&logoColor=000000" />
  <img src="https://img.shields.io/badge/Token-6f42c1?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/ERC--20-0ea5e9?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/ERC--721-9333ea?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Stablecoin-16a34a?style=for-the-badge&logo=tether&logoColor=white" />
  <img src="https://img.shields.io/badge/Tokenomics-9932CC?style=for-the-badge&logo=stackshare&logoColor=white" />

</p>

---

## 🧠 Smart Contracts
<p align="center">
  <img src="https://img.shields.io/badge/Smart%20Contracts-6f42c1?style=for-the-badge&logo=solidity&logoColor=white" />
  <img src="https://img.shields.io/badge/EVM-0284c7?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Gas-f97316?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Oracles-0ea5e9?style=for-the-badge&logo=chainlink&logoColor=white" />
</p>

---

## 🏦 DeFi
<p align="center">
  <img src="https://img.shields.io/badge/DEX-9333ea?style=for-the-badge&logo=uniswap&logoColor=white" />
  <img src="https://img.shields.io/badge/Lending-059669?style=for-the-badge&logo=aave&logoColor=white" />
  <img src="https://img.shields.io/badge/Yield%20Farming-16a34a?style=for-the-badge&logo=compound&logoColor=white" />
  <img src="https://img.shields.io/badge/Staking-4ade80?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Liquidity%20Pools-f43f5e?style=for-the-badge&logo=uniswap&logoColor=white" />
</p>

---

## 🎨 NFTs & Métadonnées
<p align="center">
  <img src="https://img.shields.io/badge/NFTs-9333ea?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/ERC--721-0ea5e9?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/IPFS-16a34a?style=for-the-badge&logo=ipfs&logoColor=white" />
  <img src="https://img.shields.io/badge/Arweave-0284c7?style=for-the-badge&logo=arweave&logoColor=white" />
</p>

---

## 🧩 DAO & Gouvernance
<p align="center">
  <img src="https://img.shields.io/badge/DAO-9333ea?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Gouvernance-0ea5e9?style=for-the-badge&logo=governance&logoColor=white" />
  <img src="https://img.shields.io/badge/Votes-16a34a?style=for-the-badge&logo=gitlab&logoColor=white" />
</p>

---

## ☁️ Infrastructure & Oracles
<p align="center">
  <img src="https://img.shields.io/badge/RPC-0284c7?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Oracles-0ea5e9?style=for-the-badge&logo=chainlink&logoColor=white" />
  <img src="https://img.shields.io/badge/Layer1-9333ea?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Layer2-f97316?style=for-the-badge&logo=polygon&logoColor=white" />
</p>


---

## 🌍 Écosystème & Réseaux
<p align="center">
  <img src="https://img.shields.io/badge/Bitcoin-FFD43B?style=for-the-badge&logo=bitcoin&logoColor=000000" />
  <img src="https://img.shields.io/badge/Ethereum-6f42c1?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Polygon-0ea5e9?style=for-the-badge&logo=polygon&logoColor=white" />
  <img src="https://img.shields.io/badge/Arbitrum-16a34a?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Solana-f97316?style=for-the-badge&logo=solana&logoColor=white" />
</p>

---

## 💼 Cas d’usage & Applications
<p align="center">
  <img src="https://img.shields.io/badge/Paiements-4ade80?style=for-the-badge&logo=visa&logoColor=white" />
  <img src="https://img.shields.io/badge/Identité%20Numérique-0284c7?style=for-the-badge&logo=digitalocean&logoColor=white" />
  <img src="https://img.shields.io/badge/Gaming-9333ea?style=for-the-badge&logo=unity&logoColor=white" />
  <img src="https://img.shields.io/badge/Supply%20Chain-0ea5e9?style=for-the-badge&logo=vechain&logoColor=white" />
</p>
