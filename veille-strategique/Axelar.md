# 🌐 Axelar — Le pont entre les blockchains (Layer 0)

## 🧩 Introduction

**Axelar Network** est une blockchain de **Layer 0**, c’est-à-dire une couche d’infrastructure qui connecte plusieurs **Layer 1** entre eux (Ethereum, Cosmos, Avalanche, Bitcoin, etc.).

Alors que les **Layer 2** visent à améliorer la **scalabilité** d’un réseau spécifique, les **Layer 0** s’attaquent à un autre défi majeur :  
➡️ **l’interopérabilité entre blockchains.**

Axelar agit comme un **réseau de transport universel** pour les messages, tokens et données entre écosystèmes hétérogènes.

---

## ⚙️ Architecture technique

Axelar repose sur une **blockchain Proof of Stake (PoS)**, construite à partir du **Cosmos SDK** et utilisant le consensus **Tendermint BFT**.  
Ce choix lui confère :
- ⛓️ Une **finalité rapide des blocs** (6-8 secondes)
- 🔐 Une **sécurité décentralisée** assurée par ses validateurs
- ⚡ Une **compatibilité native** avec l’écosystème **Cosmos / IBC**

### 🔄 Les composants principaux

| Composant | Rôle |
|------------|------|
| **Validator Nodes** | Sécurisent la blockchain Axelar, valident les messages et participent au consensus PoS |
| **Gateways** | Smart contracts déployés sur les blockchains externes (Ethereum, Avalanche, etc.) qui reçoivent et envoient les messages inter-chain |
| **Relayers** | Transmettent les données entre les Gateways et la blockchain Axelar |
| **Cross-Chain Gateway Protocol (CGP)** | Protocole qui normalise le format des messages inter-chaînes |
| **General Message Passing (GMP)** | Permet d’envoyer des instructions (non seulement des tokens) d’une chaîne à l’autre |

---

## 💬 Fonctionnement du transfert inter-chain

1. Une **transaction** est initiée sur une blockchain source (ex : Ethereum).  
2. Le smart contract **Gateway** d’Axelar reçoit la demande (ex : transfert de token ou exécution de fonction).  
3. Les **validateurs Axelar** observent l’événement et le confirment sur la blockchain Axelar.  
4. Une fois validée, la transaction est **relayée vers la blockchain cible** (ex : Avalanche).  
5. Le smart contract **Gateway cible** exécute l’action correspondante.

🔐 Chaque étape est **signée et validée collectivement** par les validateurs PoS, garantissant l’authenticité et l’unicité du message.

---

## 💡 General Message Passing (GMP)

Le protocole GMP d’Axelar permet d’envoyer des **messages arbitraires** entre blockchains.  
Exemples d’usages :
- Appeler une **fonction d’un smart contract** sur une autre blockchain  
- Transférer des **NFT cross-chain**  
- Synchroniser des **positions DeFi** entre plusieurs écosystèmes  

Ce système fait d’Axelar une **infrastructure universelle de communication inter-chain**, au-delà du simple transfert d’actifs.

---

## 🔐 Sécurité et gouvernance

- **Consensus :** Proof of Stake basé sur Tendermint → sécurité proportionnelle au staking total des validateurs  
- **Finalité rapide :** quelques secondes après inclusion du bloc  
- **Gouvernance :** les détenteurs du token **AXL** peuvent voter sur les mises à jour du protocole, les intégrations de nouvelles chaînes ou les paramètres du réseau  
- **Audits :** smart contracts Gateways audités par des tiers de confiance (ex : Halborn, Zellic)

---

## 🤝 Partenariats stratégiques

Axelar a noué des alliances dans deux sphères complémentaires :

### 🌐 Web3
- **Ripple**, **Manta**, **TON** → intégration de connexions inter-chain entre leurs réseaux  
- **Cosmos**, **Polygon**, **Avalanche**, **Moonbeam** → support natif du protocole GMP  

### 🏦 Web2 / Institutions
- **Microsoft**, **Mastercard**, **Deutsche Bank** → exploration de cas d’usage autour de la communication inter-chaîne et du Web3 d’entreprise

---

## 💹 Tokenomics (AXL)

| Élément | Détail |
|----------|--------|
| **Nom** | Axelar Token (AXL) |
| **Rôle** | Gouvernance, staking, paiement des frais inter-chain |
| **Consensus** | Proof of Stake |
| **Utilité principale** | Sécurisation du réseau et validation des messages cross-chain |
| **Frais** | Payés en AXL ou parfois en token natif de la chaîne source |

---

## 📊 Adoption et perspectives

Les éléments à surveiller :
- 📈 Nombre croissant d’intégrations DeFi utilisant GMP  
- 🔗 Déploiement sur de nouvelles blockchains (ex : Solana, Base, Sui)  
- 🧠 Évolution du volume de messages inter-chain traités  
- 🌍 Croissance de la demande d’interopérabilité cross-chain  

Avec l’expansion du **multichain Web3**, Axelar pourrait devenir une **infrastructure standard** de communication entre blockchains.

## 🏷️ Mots-clés
`#Axelar` `#Layer0` `#Blockchain` `#Interoperability` `#Cosmos` `#Tendermint` `#Web3` `#Alyra`
