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


---

## 🪙 Tokens & Cryptomonnaies
<p align="center">
  <img src="https://img.shields.io/badge/Coin-FFD43B?style=for-the-badge&logo=bitcoin&logoColor=000000" />
  <img src="https://img.shields.io/badge/Token-6f42c1?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/ERC--20-0ea5e9?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/ERC--721-9333ea?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Stablecoin-16a34a?style=for-the-badge&logo=tether&logoColor=white" />
  <img src="https://img.shields.io/badge/Tokenomics-9932CC?style=for-the-badge&logo=stackshare&logoColor=white" />
  <img src="https://img.shields.io/badge/IPFS-16a34a?style=for-the-badge&logo=ipfs&logoColor=white" />
  <img src="https://img.shields.io/badge/Arweave-0284c7?style=for-the-badge&logo=arweave&logoColor=white" />
  
## 💰 Tokens & Tokenomics

---

### 🪙 Coin

Un **coin** est une **monnaie native d’une blockchain**.  
Il possède sa **propre infrastructure**, son **réseau de nœuds** et son **mécanisme de consensus**.

🔹 Exemples :  
- **BTC** → Coin natif du réseau **Bitcoin**  
- **ETH** → Coin natif du réseau **Ethereum**  
- **BNB**, **ADA**, **SOL** → Coins de leurs propres blockchains

🧩 Les coins servent principalement à :
- Payer les frais de transaction (gas)
- Participer à la sécurité du réseau (staking / minage)
- Servir de réserve de valeur ou d’actif de base pour les tokens

---

### 🧾 Token

Un **token** est un **actif numérique émis sur une blockchain existante**.  
Il n’a pas sa propre chaîne, mais **exploite l’infrastructure d’une autre** (souvent Ethereum).

🔹 Exemple :  
Le token **USDT (Tether)** circule sur Ethereum, Polygon, BNB Chain…  
mais **dépend des règles techniques** de la blockchain sur laquelle il est déployé.

Les tokens peuvent représenter :
- 💵 **Des actifs financiers** (stablecoins, jetons d’investissement)  
- 🎟️ **Des droits d’accès** (utility tokens, DAO)
- 🎨 **Des objets uniques** (NFT)
- 🗳️ **Des droits de gouvernance** (vote dans un protocole)

---

### 🧠 Différence Coin / Token

| Caractéristique | Coin | Token |
|------------------|------|--------|
| Blockchain propre | ✅ Oui | ❌ Non |
| Fonction principale | Moyen d’échange, gas | Utilité, gouvernance, valeur |
| Exemple | BTC, ETH, SOL | USDT, UNI, LINK, AAVE |
| Création | Par protocole natif | Par smart contract |

---

### 📜 ERC-20 — Standard des tokens fongibles

L’**ERC-20** est un **standard Ethereum** qui définit les règles de création des **tokens fongibles**, c’est-à-dire **interchangeables et divisibles**.  

🔧 Fonctions principales d’un ERC-20 :
- `totalSupply()` → Nombre total de tokens créés  
- `balanceOf(address)` → Solde d’une adresse  
- `transfer(address, amount)` → Envoi de tokens  
- `approve(address, amount)` / `transferFrom()` → Autorisations de transfert (utile pour les DApps et DEX)

💡 Les tokens ERC-20 sont utilisés pour :
- Les **DeFi protocols** (Aave, Uniswap, Compound)  
- Les **tokens de gouvernance**  
- Les **stablecoins** (USDC, DAI)

🔹 Exemple :  
UNI (Uniswap), LINK (Chainlink), AAVE, COMP, SAND, etc.

---

### 🖼️ ERC-721 — Standard des tokens non fongibles (NFT)

L’**ERC-721** définit les règles des **tokens uniques** — non interchangeables.  
Chaque token possède un **identifiant (ID)** et des **métadonnées distinctes**.

🔹 Caractéristiques :
- Un token = un objet unique (œuvre, billet, item, terrain, etc.)  
- Transférable, mais **non divisble**  
- Les métadonnées (image, nom, description) sont souvent stockées sur **IPFS**

🔧 Fonctions clés :
- `ownerOf(tokenId)` → Propriétaire du token  
- `tokenURI(tokenId)` → Métadonnées associées  
- `transferFrom()` → Transfert du NFT  

💡 Exemples :  
- NFT d’art (OpenSea, Foundation)  
- Domaines ENS  
- Objets de jeux blockchain (Axie Infinity, Sandbox)

---

### 💵 Stablecoin

Les **stablecoins** sont des tokens ERC-20 (ou équivalents) conçus pour **rester stables en valeur**, souvent **adossés à une monnaie fiduciaire** comme le dollar.

🔹 Types de stablecoins :
| Type | Description | Exemple |
|------|--------------|----------|
| 💰 Collatéralisé par fiat | Réserves réelles en USD | USDT, USDC |
| 🪙 Collatéralisé par crypto | Sur-collatéralisé avec ETH, BTC | DAI (MakerDAO) |
| ⚖️ Algorithmique | Géré par smart contract et algorithme | UST (abandonné), FRAX |

💡 Intérêt :
- Faciliter les échanges sans volatilité  
- Moyen de paiement stable pour les DApps  
- Utilisé massivement dans la DeFi

---

### 📈 Tokenomics

La **Tokenomics** (Token + Economics) regroupe **tous les aspects économiques d’un token** :
- Sa création  
- Sa distribution  
- Son utilité  
- Sa rareté  
- Ses mécanismes d’incitation et de gouvernance  

---

#### ⚙️ Composants principaux

| Élément | Description |
|----------|--------------|
| 🧮 **Supply totale** | Nombre maximum de tokens existants |
| 🪙 **Circulating supply** | Tokens actuellement en circulation |
| 🔥 **Burn / Inflation** | Mécanisme de destruction ou d’émission |
| 🎁 **Distribution** | Répartition entre fondateurs, investisseurs, communauté |
| 🏦 **Utilité** | Paiement, staking, gouvernance, accès à un service |
| 🗳️ **Gouvernance** | Pouvoir de vote sur les décisions du protocole |
| 💰 **Staking / Reward** | Récompenses pour la participation au réseau |

---

#### 💡 Exemple simplifié :
Un protocole peut :
- Émettre **1 milliard de tokens max**
- En distribuer 40 % à la communauté, 30 % à l’équipe, 20 % aux investisseurs, 10 % à la trésorerie DAO
- Prévoir un **burn automatique** à chaque transaction pour maintenir la rareté
- Récompenser les utilisateurs actifs (liquidity mining, airdrops, staking)


#### 🧩 IPFS (InterPlanetary File System)
- Un **protocole de stockage décentralisé** qui remplace les adresses classiques (URLs) par des **hashs de contenu**.  
- Les fichiers sont partagés entre nœuds :  
  > Chaque fichier est découpé, distribué et identifié par un hash unique.  
- Si un fichier change, son hash change également → **authenticité garantie**.  
- Très utilisé pour stocker les **métadonnées des NFTs** (images, descriptions, JSON).

💡 Exemple :  
`ipfs://QmTzQ1...` → lien vers un contenu distribué.

#### 🧱 Arweave
- Un **réseau de stockage permanent** (blockchain orientée données).  
- Permet de **stocker des fichiers pour toujours** grâce à un paiement unique initial.  
- Idéal pour les **NFTs**, archives, ou données devant rester **immuables et disponibles à long terme**.  
- Chaque donnée est intégrée dans la **"permaweb"** (web permanent).

💡 Différence principale :
| Système | Type de stockage | Durée | Idéal pour |
|----------|------------------|--------|-------------|
| IPFS | Décentralisé par hash | Tant que des nœuds l’hébergent | Métadonnées NFT, médias |
| Arweave | Blockchain dédiée | Permanent | Archives, œuvres, données durables |

---
</p>

---

## 🧠 Smart Contracts
<p align="center">
  <img src="https://img.shields.io/badge/Smart%20Contracts-6f42c1?style=for-the-badge&logo=solidity&logoColor=white" />
  <img src="https://img.shields.io/badge/EVM-0284c7?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Gas-f97316?style=for-the-badge&logo=ethereum&logoColor=white" />
</p>

---

### 📜 Smart Contract

Un **smart contract** est un **programme informatique stocké sur la blockchain**.  
Il s’exécute automatiquement lorsque certaines conditions sont remplies, **sans intermédiaire**.

🧩 Exemple :
> "Si Alice envoie 1 ETH à Bob, alors transférer un NFT à Alice."

Ces contrats permettent d’automatiser :
- Les paiements 💸  
- Les échanges de tokens 🔄  
- Les prêts / emprunts (DeFi) 🏦  
- Les votes (DAO) 🗳️  

💡 Une fois déployé, le code est **public, immuable et transparent**.

---

### 🔥 Gas (frais de transaction)

Chaque action sur la blockchain (envoi, déploiement, calcul) consomme du **gas**,  
une unité qui mesure la **puissance de calcul utilisée**.

- Le **gas** se paie en **ETH**.  
- Plus un contrat est complexe, plus il consomme de gas.  
- Les utilisateurs peuvent fixer un **gas limit** (quantité max de calcul) et un **gas price** (prix par unité).

🧮 Coût total = `Gas used × Gas price`

💡 Le gas :
- Empêche les boucles infinies  
- Rétribue les validateurs  
- Garantit la sécurité du réseau

---

### 🧠 EVM — Ethereum Virtual Machine

L’**EVM (Ethereum Virtual Machine)** est le **moteur qui exécute les smart contracts** sur Ethereum.  
Tous les nœuds du réseau possèdent une copie de l’EVM.

> Elle traduit le code du contrat (écrit en **Solidity**) en **bytecode** compréhensible par la blockchain.

🧩 Rôle de l’EVM :
- Exécuter les contrats de manière identique sur tous les nœuds  
- Gérer l’état global de la blockchain (soldes, données, stockage)  
- Garantir que les règles sont respectées et que chaque transaction est valide  


---

## 🏦 DeFi
<p align="center">
  <img src="https://img.shields.io/badge/DEX-9333ea?style=for-the-badge&logo=uniswap&logoColor=white" />
  <img src="https://img.shields.io/badge/Lending-059669?style=for-the-badge&logo=aave&logoColor=white" />
  <img src="https://img.shields.io/badge/Yield%20Farming-16a34a?style=for-the-badge&logo=compound&logoColor=white" />
  <img src="https://img.shields.io/badge/Staking-4ade80?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Liquidity%20Pools-f43f5e?style=for-the-badge&logo=uniswap&logoColor=white" />
</p>

## 💸 DeFi — Finance Décentralisée

---

### 🌐 Définition

La **DeFi (Decentralized Finance)** désigne l’ensemble des **services financiers construits sur la blockchain**,  
accessibles à tous, **sans banque ni intermédiaire**.

Ces services fonctionnent grâce aux **smart contracts**, qui automatisent :
- Les échanges de tokens (DEX)  
- Les prêts / emprunts (Lending)  
- Le staking et les pools de liquidité  
- La génération de rendement (Yield Farming)

---

### 🏦 DEX — Exchange Décentralisé

Un **DEX (Decentralized Exchange)** permet d’échanger des tokens **directement entre utilisateurs**, sans tiers de confiance.

Les échanges se font via des **smart contracts** appelés **AMM (Automated Market Makers)**.

💡 Principe :
- Les utilisateurs déposent deux tokens (ex : ETH / USDC) dans une **liquidity pool**.
- Les traders échangent contre cette réserve.
- Le prix est calculé par une formule automatique, souvent :
x * y = k

(constante d’équilibre entre les deux actifs).

🔹 Exemples : **Uniswap**, **SushiSwap**, **Curve**, **Balancer**

---

### 💰 Lending & Borrowing

Les protocoles de **lending (prêt)** et **borrowing (emprunt)** permettent de **déposer des tokens** pour en percevoir des intérêts ou **emprunter d’autres actifs**.

💡 Fonctionnement :
- L’utilisateur dépose des tokens → ils sont verrouillés dans un **smart contract**.  
- En échange, il reçoit des **intérêts** (souvent en stablecoins).  
- Un emprunteur peut déposer une **garantie (collatéral)** pour emprunter d’autres tokens.

🔹 Exemples : **Aave**, **Compound**, **Venus**

> ⚠️ En cas de baisse du collatéral sous un certain seuil, la position est **liquidée automatiquement**.

---

### 🌾 Yield Farming

Le **Yield Farming** consiste à **placer ses tokens dans plusieurs protocoles DeFi** pour générer un **rendement maximal**.  
Les utilisateurs (“farmers”) déplacent leurs fonds entre plateformes pour profiter des meilleures récompenses.

💡 Exemples de stratégies :
- Fournir de la liquidité sur un DEX (Uniswap, Curve)
- Staker les tokens reçus en échange (LP Tokens)
- Gagner des intérêts, plus des **récompenses en tokens du protocole**

> 🚜 En résumé : tu “cultives” ton rendement en déplaçant tes tokens dans différents “champs” DeFi.

---

### 🔒 Staking

Le **staking** consiste à **verrouiller ses tokens** pour **participer à la sécurité d’un réseau** (Proof of Stake)  
et **recevoir des récompenses** en échange.

💡 Deux types :
- **Staking réseau (PoS)** → Sécurise la blockchain (ex : Ethereum, Polygon, Cardano)  
- **Staking DeFi** → Dépôt sur un protocole pour générer des intérêts  

🔹 Exemples :  
- Staking ETH via **Lido**, **Rocket Pool**  
- Staking DeFi sur **Aave**, **Curve**, **PancakeSwap**

> Les rendements varient selon la durée, le protocole et le risque de volatilité.

---

### 💧 Liquidity Pool

Une **liquidity pool** est une **réserve de tokens bloqués** dans un smart contract.  
Elle permet :
- Aux utilisateurs d’échanger des tokens (DEX)  
- Aux protocoles de prêter ou emprunter (Lending)  
- De générer des récompenses pour les fournisseurs de liquidité (LP)

💡 Exemple :
Une pool ETH/USDC sur Uniswap contient 50 % d’ETH et 50 % d’USDC.  
Chaque trade fait varier le ratio des deux actifs, ce qui ajuste automatiquement le prix.

🔹 Les **liquidity providers (LPs)** gagnent une part des **frais de transaction** générés.

⚠️ Risque principal : **impermanent loss**  
> Perte temporaire liée à la variation du prix des actifs dans la pool.


---

## 🧩 DAO & Gouvernance
<p align="center">
  <img src="https://img.shields.io/badge/DAO-9333ea?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Gouvernance-0ea5e9?style=for-the-badge&logo=governance&logoColor=white" />
  <img src="https://img.shields.io/badge/Votes-16a34a?style=for-the-badge&logo=gitlab&logoColor=white" />
</p>

## 🗳️ Gouvernance & DAO

---

### 🧠 Gouvernance dans la blockchain

La **gouvernance** désigne la **manière dont les décisions sont prises** au sein d’un protocole ou d’une communauté blockchain.  
Elle permet aux détenteurs de tokens de **proposer, voter et influencer** l’évolution d’un projet.

Deux grands types de gouvernance existent :
- **On-chain** → Les votes et décisions sont enregistrés directement sur la blockchain via des smart contracts.  
- **Off-chain** → Les discussions et votes ont lieu en dehors de la blockchain (forums, Snapshot, Discord), puis sont appliqués manuellement.

💡 Objectif :
> Remplacer les décisions centralisées (d’une entreprise) par un **modèle communautaire décentralisé**.

---

### 🏛️ DAO — Decentralized Autonomous Organization

Une **DAO (Organisation Autonome Décentralisée)** est une **communauté gouvernée par des smart contracts**.  
Les règles sont inscrites dans le code, et les décisions se prennent collectivement grâce aux détenteurs de tokens.

#### 🔧 Fonctionnement :
1. Les membres détiennent un **token de gouvernance** (ex : UNI, AAVE, COMP).  
2. Chaque token représente **un droit de vote**.  
3. Les propositions (améliorations, budgets, partenariats) sont soumises et votées par la communauté.  
4. Si la proposition atteint le quorum requis → elle est **adoptée automatiquement** via un smart contract.

💡 Une DAO agit comme une **entreprise sans dirigeant unique**, où le pouvoir est distribué entre les participants.

🔹 Exemples :
- **Uniswap DAO** → Gère les évolutions du protocole et la trésorerie.  
- **MakerDAO** → Pilote la création du stablecoin DAI.  
- **Aave DAO** → Vote sur les paramètres de prêt et la gestion des risques.  

---

### 🗳️ Les votes et la gouvernance on-chain

Les votes sont exécutés par des **smart contracts de gouvernance**.  
Chaque proposition suit un processus clair :

#### ⚙️ Étapes typiques :
1. **Proposition (Proposal)** — un membre soumet une idée ou une amélioration.  
2. **Période de vote** — les détenteurs de tokens votent "Pour", "Contre" ou "Abstention".  
3. **Quorum** — un minimum de participation est requis pour valider le vote.  
4. **Exécution** — si le vote est validé, le smart contract applique automatiquement la décision.

#### 💡 Types de votes :
| Type | Description |
|------|--------------|
| 🧮 **1 token = 1 vote** | Modèle classique (pondéré par la détention de tokens) |
| 👥 **Quadratic voting** | Système qui donne plus de poids aux petits détenteurs |
| 🧾 **Delegated voting** | Les votes peuvent être délégués à un représentant |

---

### 🪙 Token de gouvernance

Un **token de gouvernance** permet à ses détenteurs :
- De **participer aux votes** de la DAO  
- De **soumettre des propositions**  
- D’obtenir une **voix dans la direction du protocole**

💡 Ces tokens ne donnent pas seulement une valeur financière,  
mais aussi un **pouvoir décisionnel** dans la communauté.

🔹 Exemples :
- **UNI** → Uniswap  
- **COMP** → Compound  
- **AAVE** → Aave  
- **MKR** → MakerDAO  


---

## ☁️ Infrastructure & Oracles
<p align="center">
  <img src="https://img.shields.io/badge/RPC-0284c7?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Oracles-0ea5e9?style=for-the-badge&logo=chainlink&logoColor=white" />
  <img src="https://img.shields.io/badge/Layer1-9333ea?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Layer2-f97316?style=for-the-badge&logo=polygon&logoColor=white" />
</p>
## 🏗️ Infrastructure & Oracles

---

### 🌍 Vue d’ensemble

L’**infrastructure blockchain** regroupe l’ensemble des couches et services techniques  
qui permettent à une blockchain de **fonctionner, communiquer et évoluer**.

On distingue plusieurs **couches (layers)** :
- **Layer 0** → Interconnexion entre blockchains  
- **Layer 1** → Blockchain principale (base du réseau)  
- **Layer 2** → Solutions de scalabilité construites au-dessus du Layer 1  
- Et des outils d’accès : **RPC** et **Oracles**

---

### 🧩 Layer 0 — L’internet des blockchains

Le **Layer 0** fournit une **infrastructure interopérable** permettant à plusieurs blockchains de communiquer entre elles.  
Il agit comme une **couche réseau** reliant différents Layer 1.

💡 Objectif :
> Créer un “pont” entre les écosystèmes pour permettre les échanges de données et d’actifs.

🔹 Exemples :
- **Axelar** → Communication inter-chain (cross-chain messaging)  
- **Polkadot** → Relie des “parachains” entre elles  
- **Cosmos (IBC)** → Connecte des blockchains indépendantes via le protocole IBC  

---

### 🧱 Layer 1 — La blockchain principale

Le **Layer 1** est la **chaîne de base** où s’exécutent les transactions et smart contracts.  
C’est elle qui définit :
- Le **consensus** (Proof of Work, Proof of Stake, etc.)  
- La **sécurité** du réseau  
- Le **token natif** (BTC, ETH, ADA…)

💡 Exemples :
- **Bitcoin**, **Ethereum**, **Solana**, **Cardano**, **Avalanche**

> Toutes les règles du protocole et la validation des blocs sont gérées ici.

---

### ⚡ Layer 2 — La surcouche de scalabilité

Le **Layer 2** améliore les performances du Layer 1 sans en modifier la sécurité.  
Il **délègue une partie du travail hors chaîne (off-chain)** puis renvoie les résultats sur la blockchain principale.

💡 Objectif :
> Augmenter la vitesse et réduire les frais de transaction.

🔹 Types de Layer 2 :
| Type | Description | Exemple |
|------|--------------|----------|
| 🧾 **State channels** | Canaux entre deux utilisateurs | Lightning Network (Bitcoin) |
| 🔒 **Rollups** | Transactions regroupées puis publiées sur L1 | Arbitrum, Optimism, zkSync |
| 💳 **Sidechains** | Chaînes parallèles reliées au L1 | Polygon PoS, Ronin |

---

### 🛰️ RPC — Remote Procedure Call

Le **RPC** est une **interface de communication** qui permet aux applications (wallets, DApps, explorateurs)  
d’interagir avec une blockchain.

💡 Exemple :  
Lorsqu’un wallet comme **Metamask** envoie une transaction, il utilise un **nœud RPC** pour :
- Lire les données de la blockchain (balance, transactions, blocs)  
- Écrire de nouvelles transactions  

🔹 Fournisseurs de RPC :
- **Infura**, **Alchemy**, **QuickNode**, **Ankr**, **Chainstack**

> En résumé : le RPC est la **porte d’entrée technique** vers la blockchain.

---

### 🔮 Oracles — La passerelle avec le monde réel

Les **oracles** sont des **services décentralisés** qui fournissent à la blockchain  
des **données externes** qu’elle ne peut pas obtenir seule (prix, météo, résultats, API…).

💡 Exemple :
> Un smart contract de DeFi peut demander à un oracle le **prix actuel de l’ETH/USD**  
> pour calculer les taux de prêt.

🔹 Types d’oracles :
| Type | Fonction | Exemple |
|------|-----------|----------|
| 📊 **Oracles de données** | Fournissent des prix, taux, infos externes | Chainlink, Pyth Network |
| 🕹️ **Oracles d’événements** | Transmettent un événement réel (match, vote, météo) | API3, Augur |
| 🔗 **Cross-chain oracles** | Relient différentes blockchains | Axelar, LayerZero |

💡 Importance :
- Permettent les **cas d’usage avancés** (DeFi, assurances, jeux, IoT)
- Doivent rester **fiables, décentralisés et audités** pour éviter les manipulations

---

## 🌍 Écosystème & Réseaux
<p align="center">
  <img src="https://img.shields.io/badge/Bitcoin-FFD43B?style=for-the-badge&logo=bitcoin&logoColor=000000" />
  <img src="https://img.shields.io/badge/Ethereum-6f42c1?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Polygon-0ea5e9?style=for-the-badge&logo=polygon&logoColor=white" />
  <img src="https://img.shields.io/badge/Arbitrum-16a34a?style=for-the-badge&logo=ethereum&logoColor=white" />
  <img src="https://img.shields.io/badge/Solana-f97316?style=for-the-badge&logo=solana&logoColor=white" />
</p>
## 🌐 Écosystèmes & Réseaux

---

### 🪙 Bitcoin — La première blockchain

Créée en **2009** par **Satoshi Nakamoto**, Bitcoin est la **première blockchain** et reste la **plus sécurisée**.  
Son objectif principal : devenir une **monnaie numérique décentralisée** et **réserve de valeur mondiale**.

💡 Caractéristiques :
- Consensus : **Proof of Work (PoW)**
- Objectif : monnaie et transfert de valeur
- Token natif : **BTC**
- Particularité : système **UTXO** (Unspent Transaction Output)
- Surcouche : **Lightning Network** pour les paiements rapides ⚡

---

### 🧠 Ethereum — L’ordinateur mondial

Lancé en **2015** par **Vitalik Buterin**, Ethereum a introduit le concept de **smart contracts**,  
permettant de créer des **applications décentralisées (DApps)**.

💡 Caractéristiques :
- Consensus : **Proof of Stake (PoS)** depuis The Merge (2022)
- Objectif : exécuter des smart contracts
- Token natif : **ETH**
- Particularité : machine virtuelle **EVM**
- Écosystème : **DeFi**, **NFT**, **DAO**, **Layer 2**

---

### ⚡ Solana — Rapidité et scalabilité

Solana est une blockchain **hautement performante**, conçue pour des **transactions rapides et peu coûteuses**.  
Elle mise sur une architecture innovante pour rivaliser avec les systèmes centralisés.

💡 Caractéristiques :
- Consensus : **Proof of History (PoH)** + **Proof of Stake (PoS)**
- Objectif : applications à haute fréquence (DeFi, jeux, IA)
- Token natif : **SOL**
- Vitesse : +50 000 transactions/seconde
- Particularité : très faible coût par transaction

---

### 🟣 Polygon — L’échelle d’Ethereum

Polygon est un **Layer 2** (et parfois sidechain) construit pour **améliorer la scalabilité d’Ethereum**.  
Il permet des **transactions plus rapides et moins coûteuses** tout en restant compatible avec l’écosystème EVM.

💡 Caractéristiques :
- Consensus : **Proof of Stake**
- Objectif : scalabilité et interopérabilité
- Token natif : **MATIC**
- Particularité : compatible EVM, utilisé par de nombreux projets DeFi/NFT
- Solutions : **Polygon PoS**, **zkEVM**, **Supernets**

---

### 🌀 Arbitrum — Le rollup d’Ethereum

Arbitrum est une solution **Layer 2** basée sur le concept de **rollup optimiste**.  
Elle permet d’exécuter des transactions **hors de la blockchain Ethereum**, puis d’enregistrer un **résumé** sur celle-ci pour garantir la sécurité.

💡 Caractéristiques :
- Type : **Optimistic Rollup**
- Objectif : réduire les frais et augmenter le débit
- Token natif : **ARB**
- Compatibilité : 100 % **EVM-compatible**
- Avantage : sécurité héritée d’Ethereum + rapidité

---

## 💼 Cas d’usage & Applications
<p align="center">
  <img src="https://img.shields.io/badge/Paiements-4ade80?style=for-the-badge&logo=visa&logoColor=white" />
  <img src="https://img.shields.io/badge/Identité%20Numérique-0284c7?style=for-the-badge&logo=digitalocean&logoColor=white" />
  <img src="https://img.shields.io/badge/Gaming-9333ea?style=for-the-badge&logo=unity&logoColor=white" />
  <img src="https://img.shields.io/badge/Supply%20Chain-0ea5e9?style=for-the-badge&logo=vechain&logoColor=white" />
</p>
## 💼 Cas d’usage & Applications

---

### 💳 Paiement & transfert de valeur

L’un des **premiers usages historiques** de la blockchain : le **paiement décentralisé**.  
Bitcoin a ouvert la voie à un système financier sans banque, où les utilisateurs échangent de la valeur **de pair à pair (P2P)**.

💡 Objectifs :
- Réduire les **frais de transaction** et les **intermédiaires**
- Faciliter les **paiements transfrontaliers**
- Offrir une **inclusion financière** mondiale

🔹 Exemples :
- **Bitcoin** → monnaie numérique mondiale  
- **Lightning Network** → paiements instantanés et à très faible coût  
- **USDT / USDC / DAI** → stablecoins pour éviter la volatilité  
- **Crypto.com**, **Binance Pay**, **BitPay** → solutions concrètes de paiement crypto

> 🌍 La blockchain permet d’envoyer de l’argent partout dans le monde,  
> 24h/24, sans autorisation, ni frontière.

---

### 🪪 Identité numérique décentralisée (DID)

L’**identité numérique décentralisée** vise à redonner à chaque individu le **contrôle de ses données personnelles**.  
Au lieu d’être stockées par des entreprises, les informations sont **liées à une clé cryptographique** que seul l’utilisateur contrôle.

💡 Fonctionnement :
- Chaque personne possède une **clé publique / clé privée**
- Les informations d’identité sont **vérifiées par des tiers de confiance**
- Les preuves (hashs) sont enregistrées sur la blockchain
- L’utilisateur choisit **quelles données partager, avec qui, et quand**

🔹 Exemples :
- **Jasmy** (IoT & data ownership au Japon)  
- **Polygon ID**, **Civic**, **Worldcoin ID**, **Lens Protocol**  
- **DID (Decentralized Identifiers)** & **Verifiable Credentials (VC)** — standards W3C

💡 Cas d’usage :
- Connexion sécurisée à des plateformes Web3  
- Accès à des services publics ou privés sans mot de passe  
- Certification d’identité, de diplôme ou de réputation on-chain

> 🧠 “Je possède mes données, je décide quand et comment elles sont partagées.”

---

### 🎮 Gaming & Metaverse

Le **Web3 gaming** intègre les tokens et NFT pour **donner une vraie propriété numérique** aux joueurs.  
Les objets, avatars ou terrains sont stockés **on-chain**, et non sur les serveurs d’une entreprise.

💡 Objectifs :
- Redonner la **valeur économique** aux joueurs  
- Permettre la **revente libre** des items ou personnages  
- Créer des **économies virtuelles ouvertes**

🔹 Exemples :
- **Axie Infinity**, **The Sandbox**, **Decentraland**, **Illuvium**
- **Enjin**, **Immutable X**, **Gala Games** → infrastructures de gaming Web3  
- Intégration de **NFTs** comme items de jeu (skins, armes, cartes)

💎 Modèles économiques :
- **Play-to-Earn** → les joueurs gagnent des tokens en jouant  
- **Own-to-Play** → la valeur réside dans la possession des actifs  
- **Metaverse** → espaces virtuels interconnectés basés sur la blockchain

> 🎮 “Dans le Web3, les joueurs deviennent propriétaires de leurs univers.”

---

### 🚚 Supply Chain & traçabilité

La blockchain révolutionne la **traçabilité des produits**, de leur fabrication à leur distribution.  
Chaque étape du cycle de vie est enregistrée de manière **transparente, infalsifiable et vérifiable**.

💡 Avantages :
- Lutte contre la **contrefaçon**  
- Amélioration de la **traçabilité alimentaire, pharmaceutique, industrielle**  
- Confiance accrue entre les acteurs de la chaîne logistique  

🔹 Fonctionnement :
1. Chaque acteur (producteur, transporteur, distributeur) enregistre ses données sur la blockchain  
2. Les produits sont identifiés par un **QR code ou puce RFID**  
3. Toutes les étapes sont consultables publiquement  

🔹 Exemples :
- **VeChain** → traçabilité pour le luxe, la santé et l’agroalimentaire  
- **IBM Food Trust** (sur Hyperledger) → suivi des produits alimentaires  
- **Provenance**, **TE-FOOD**, **OriginTrail**

💡 Cas d’usage :
- Suivre l’origine du café, du vin, ou des médicaments  
- Vérifier l’authenticité d’un article de luxe  
- Automatiser la logistique via des smart contracts  

> 📦 “De la ferme à l’assiette, chaque étape est enregistrée, transparente et vérifiable.”

---
