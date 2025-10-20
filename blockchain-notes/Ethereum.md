# 🧠  Ethereum : Histoire, Machine à États, Proof of Stake & Architecture du Réseau

## 🏛️ 1. Histoire et vision d’Ethereum

Ethereum a été imaginé par **Vitalik Buterin** en 2013 et lancé officiellement en **2015**.  
Son objectif : aller au-delà du simple transfert de valeur (comme sur Bitcoin) en créant une **blockchain programmable** capable d’exécuter des **smart contracts** — des programmes autonomes stockés et exécutés sur la blockchain.

L’idée clé : faire d’Ethereum une **“machine à états mondiale”**, partagée entre des milliers de nœuds.

### 🪶 Évolution du protocole
| Étape | Année | Objectif |
|-------|--------|-----------|
| **Frontier** | 2015 | Première version publique |
| **Homestead** | 2016 | Stabilisation du réseau |
| **Byzantium / Constantinople / Istanbul** | 2017–2019 | Optimisations, base du futur PoS |
| **The Merge** | 2022 | Passage du Proof of Work au Proof of Stake |
| **Dencun Upgrade** | 2024 | Proto-Danksharding & réduction du coût des rollups |

---

## 🧩 2. Comptes, adresses et états

Sur Ethereum, tout tourne autour d’un **état global** : le registre de toutes les adresses, soldes et smart contracts.

### 👤 Deux types de comptes :
1. **EOA (Externally Owned Account)**  
   - Contrôlé par une clé privée.  
   - Peut initier des transactions.  
   - Exemple : ton portefeuille Metamask.

2. **Contract Account**  
   - Possède du code exécuté par l’EVM.  
   - Ne peut agir que lorsqu’il est appelé par une transaction ou un autre contrat.

Chaque compte contient :
**nonce** → nombre de transactions envoyées
**balance** → solde en wei (1 ETH = 10¹⁸ wei)
**storageRoot** → hash de l’état interne du contrat
**codeHash** → hash du bytecode EVM


L’ensemble de ces informations forme l’**état global**, stocké dans un arbre de **Merkle Patricia Trie** (une structure qui permet de prouver les états sans tout télécharger).

---

## ⚙️ 3. Machine à états et registre distribué

Ethereum fonctionne comme une **machine à états** :  
Chaque transaction applique une fonction de transition sur l’état global.

Chaque nœud du réseau conserve une **copie identique de l’état final** après chaque bloc.  
C’est ce qui garantit la cohérence du registre sans autorité centrale.

---

## 🔗 4. Transactions, blocs et gas

### 🧾 Structure d’une transaction
Une transaction contient :

nonce, gasPrice, gasLimit, to, value, data, v, r, s

- `nonce` : empêche la double dépense.  
- `gasPrice` : prix du gas par unité.  
- `gasLimit` : quantité maximale de gas autorisée.  
- `to` : adresse du destinataire ou du contrat.  
- `data` : code ou appel de fonction (ABI encodé).  
- `(v, r, s)` : signature cryptographique ECDSA.

### ⛽ Le Gas
Le **gas** est l’unité de mesure du coût de calcul sur Ethereum.  
Chaque opération dans la **EVM** consomme du gas (ex : `ADD` = 3 gas, `SSTORE` = 20 000 gas).  

- Si la transaction dépasse le `gasLimit`, elle échoue (mais le gas est quand même dépensé).  
- Le gas sert à rémunérer les validateurs et à éviter les boucles infinies.

### 🧱 Structure d’un bloc

header:
parentHash
stateRoot
transactionsRoot
receiptsRoot
timestamp
baseFeePerGas
...
transactions:
[TX1, TX2, TX3...]


Chaque bloc référence le précédent via `parentHash`, formant ainsi la **blockchain**.

---

## 🔒 5. Proof of Stake et Staking

Depuis **The Merge (2022)**, Ethereum fonctionne en **Proof of Stake (PoS)** via la **Beacon Chain**.  

### 🧠 Principe
- Les **validateurs** doivent déposer **32 ETH** dans le contrat de staking.  
- Ils sont sélectionnés aléatoirement pour proposer ou attester des blocs.  
- Les comportements malhonnêtes entraînent des **slashing penalties** (perte partielle ou totale des ETH stakés) :

- ### ⚔️ Les 3 types de sanctions d’un nœud validateur sur Ethereum (Proof of Stake)



### ⚠️ 1. Pénalité de performance (Inactivity Leak)

**Cause :**  
Le validateur est **hors ligne**, ne propose pas de blocs, ou ne signe pas les attestations pendant plusieurs epochs.

**Effet :**  
- Perte progressive de récompenses.  
- Pas de slashing direct, mais un **leak** continu du solde en ETH.  
- Si le réseau connaît un manque de finalité prolongé, les pénalités augmentent exponentiellement.

**But :**  
Encourager la disponibilité permanente des nœuds et dissuader la négligence.

**Exemple :**
Validateur en ligne 99 % du temps → pertes négligeables
Validateur offline 24h → perte ≈ 0.01 ETH
Validateur offline 7 jours → pertes significatives

---

### 🚫 2. Slashing partiel (Faute de consensus)

**Cause :**  
Le validateur agit de manière incohérente avec le consensus, par exemple :

- Propose deux blocs différents pour le même slot.

- Atteste deux chaînes contradictoires.

- Signe des messages invalides ou divergents.


**Effet :**  
- Perte **immédiate d’une partie des ETH stakés** (entre 0.5 et 3 ETH selon la gravité).  
- **Expulsion automatique** du rôle de validateur après une période de pénalité (*withdrawal period*).  
- Le validateur reste inscrit comme “slashed” dans la Beacon Chain (traçable publiquement).

**But :**  
Préserver l’intégrité du consensus et empêcher la double validation ou les forks malveillants.

---

### 💀 3. Slashing massif (Comportement coordonné malveillant)

**Cause :**  
Plusieurs validateurs appartenant au même opérateur ou groupe **commettent la même faute simultanément**, par exemple :

Signer collectivement des blocs contradictoires.

Tenter une attaque de réorganisation (reorg) ou de censure.

Envoyer des attestations conflictuelles en masse.


**Effet :**  
- Le protocole augmente la **pénalité en fonction du nombre de validateurs fautifs**.  
- Peut entraîner la **perte totale du stake (jusqu’à 32 ETH)** par validateur.  
- Les fautifs sont immédiatement expulsés du réseau.

**But :**  
Dissuader les attaques coordonnées et rendre toute malveillance économiquement suicidaire.

---

## 🧠 Résumé des sanctions

| Type de sanction | Gravité | Cause principale | Conséquence |
|------------------|----------|------------------|--------------|
| **Inactivity Leak** | ⚙️ Faible | Hors ligne / inactif | Perte progressive de récompenses |
| **Slashing partiel** | 🔥 Moyenne | Double proposition / attestation contradictoire | Perte de plusieurs ETH + expulsion |
| **Slashing massif** | 💀 Critique | Attaque coordonnée / malveillance | Perte totale du stake + expulsion immédiate |

---



### 💰 Récompenses
Les validateurs reçoivent des récompenses pour :
- proposer un bloc valide,  
- attester les blocs des autres,  
- participer au consensus via les *committees*.  

Le rendement dépend :
- du nombre total d’ETH stakés,  
- du temps de disponibilité du validateur,  
- de la participation au consensus.

Les validateurs sont récompensés en ETH nouvellement créés et via les **frais de transaction (gas fees)**.

---

## ⚙️ 6. — Les protocoles de consensus sur Ethereum : Casper FFG & LMD-GHOST

### 🧩 Introduction

Depuis **The Merge** (septembre 2022), Ethereum repose sur un consensus hybride **Proof of Stake (PoS)** combinant deux protocoles complémentaires :

- 🧱 **Casper FFG (Friendly Finality Gadget)** — gère la *finalité* des blocs  
- 🌐 **LMD-GHOST (Latest Message Driven - Greediest Heaviest Observed SubTree)** — gère le *choix de la tête de chaîne* (le “head block”)

Ces deux mécanismes travaillent ensemble au sein de la **Beacon Chain** pour assurer la sécurité, la cohérence et la finalité du réseau Ethereum PoS.

---

### 🔒 1. Casper FFG — Finalité des blocs

#### 💡 Objectif
Casper FFG (Friendly Finality Gadget) permet de **déterminer à quel moment un bloc devient irréversible** — c’est-à-dire finalisé.

Un bloc finalisé **ne peut plus être annulé** à moins de punir financièrement une majorité de validateurs (slashing massif).

#### ⚙️ Fonctionnement général
Casper FFG fonctionne sur la base d’un système de **checkpoints** (points de repère sur la chaîne).

- Tous les **32 slots (~6,4 minutes)**, Ethereum définit une nouvelle *epoch*.
- Dans chaque epoch, certains blocs deviennent des **checkpoints candidats**.
- Les validateurs **votent** pour lier un checkpoint à celui de l’epoch précédente.
- Si **au moins 2/3 des validateurs** attestent la même chaîne, le checkpoint devient :
  - **Justifié** → validé temporairement.
  - **Finalisé** → irréversible si le suivant est justifié à son tour.

#### 🧮 Résumé du processus
1. Les validateurs émettent des **attestations** sur les checkpoints.  
2. Un checkpoint est *justifié* quand ≥ 2/3 des votes le soutiennent.  
3. Un checkpoint *justifié* devient *finalisé* lorsque le suivant est justifié.  
4. Une fois finalisé → aucune réorganisation (reorg) n’est possible sans pertes économiques majeures.

#### 🔐 Sécurité
- Finalité garantie **économiquement** : pour revenir en arrière, un attaquant doit perdre au moins **1/3 du total staké**.  
- Cela rend les attaques coûteuses, donc dissuasives.  

---

### ⚙️ 2. LMD-GHOST — Choix de la tête de chaîne

#### 💡 Objectif
LMD-GHOST (Latest Message Driven - Greediest Heaviest Observed SubTree) est l’algorithme utilisé pour déterminer **quel bloc est le “head” de la blockchain** — c’est-à-dire la version la plus récente et valide.

Alors que Casper gère la *finalité*, LMD-GHOST gère la *construction continue* de la chaîne.

#### 🧠 Principe de base
Chaque validateur envoie régulièrement un **vote (attestation)** pour indiquer :
- quel bloc il considère comme la tête actuelle,  
- et à quel parent celui-ci est relié.

LMD-GHOST parcourt ensuite l’arbre des blocs et choisit la **chaîne ayant le plus grand poids de votes récents** (les “latest messages”).

> “Greediest Heaviest Observed SubTree” = on suit toujours la branche la plus lourde (celle qui a reçu le plus d’attestations récentes).

#### 🔄 Étapes simplifiées
1. Le validateur analyse tous les votes récents des autres nœuds.  
2. Il part du dernier bloc *justifié* par Casper.  
3. Il remonte l’arbre des blocs et suit **à chaque étape la branche ayant le plus de poids (votes)**.  
4. Le dernier bloc de cette branche devient la **tête de chaîne**.  

#### ⚡ Avantages
- Permet un consensus **rapide et réactif**, même avec un grand nombre de validateurs.  
- Réduit les risques de forks temporaires.  
- Assure une **cohérence** entre la chaîne canonique (LMD-GHOST) et la chaîne finalisée (Casper FFG).

---

### 🧩 3. Complémentarité des deux protocoles

| Rôle | Casper FFG | LMD-GHOST |
|------|-------------|------------|
| 🏁 **But principal** | Déterminer la finalité économique d’un bloc | Déterminer la tête actuelle de la chaîne |
| ⏱ **Fréquence** | Par epoch (~6,4 min) | À chaque slot (~12 s) |
| 🗳 **Basé sur** | Votes de 2/3 des validateurs | Votes les plus récents (latest messages) |
| 🔐 **Effet** | Rendre un bloc irréversible | Maintenir une chaîne cohérente et vivante |
| ⚙️ **Interaction** | Fournit le dernier bloc “justifié” à LMD-GHOST | Continue la chaîne depuis ce bloc justifié |

En résumé :
> 🧠 **LMD-GHOST construit la chaîne**,  
> 💎 **Casper FFG la finalise.**

---

### 🚀 Conclusion

Le consensus actuel d’Ethereum repose sur une **synergie entre Casper FFG et LMD-GHOST** :
- LMD-GHOST garantit que les validateurs convergent rapidement sur une seule tête de chaîne cohérente.  
- Casper FFG assure que cette chaîne devient **finale, immuable et économiquement sécurisée**.

Cette combinaison offre à Ethereum un **équilibre entre rapidité, sécurité et décentralisation**, tout en supprimant la lourde consommation énergétique du Proof of Work.

> 🔗 Ethereum n’est donc plus seulement une blockchain décentralisée —  
> c’est un **système de consensus hybride intelligent**, pensé pour durer à grande échelle.

## 🧮 7. L’EVM : Ethereum Virtual Machine

L’**EVM** (Ethereum Virtual Machine) est une machine virtuelle déterministe et isolée qui exécute le **bytecode** des smart contracts.

### ⚡ Caractéristiques
- Turing-complete (peut exécuter tout calcul logique).  
- Basée sur une pile (stack-based VM).  
- Chaque instruction a un coût en gas fixe.  
- Le **storage** est persistant, la **memory** est temporaire (par appel).  

Exemple simple d’exécution :
PUSH 2
PUSH 3
ADD

Résultat dans la pile : `5`  

Chaque nœud exécute le même code → **consensus sur l’état final**.

---

## 🌍 8. Vision globale

Ethereum, c’est :
- Un **registre d’état distribué**,  
- Une **machine virtuelle partagée**,  
- Un **système économique incitatif** (gas, staking, récompenses),  
- Un **écosystème de contrats interopérables**.  

C’est la base de toute l’économie décentralisée moderne : **DeFi**, **NFT**, **DAO**, **Layer 2**, **Rollups**, etc.

---

## 🧾 9. Schéma simplifié du fonctionnement

Utilisateur → Transaction → Réseau → Bloc → EVM → État mis à jour

