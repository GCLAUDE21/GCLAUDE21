# ₿ Bitcoin — Notes Techniques (Semaines 1 & 2 - Alyra)

> **Formation Consultant Blockchain - Alyra**  
> Auteur : Guillaume  
> 📅 Octobre 2025  
> 📘 Thème : Étude technique du protocole Bitcoin (couches fondamentales, consensus, cryptographie, UTXO)

---

## 🧱 Introduction

**Bitcoin (BTC)** est la **première blockchain publique décentralisée**.  
Imaginée en **2008** par *Satoshi Nakamoto* dans le white paper _"Bitcoin: A Peer-to-Peer Electronic Cash System"_,  
elle vise à créer un **système de paiement électronique pair-à-pair** permettant d’envoyer de la valeur **sans tiers de confiance**.

🔑 **Objectif fondamental :**  
> "Un système monétaire décentralisé et inviolable, fondé sur la cryptographie et la preuve de travail."

Bitcoin repose sur **trois piliers techniques :**
1. 🌐 Un **réseau pair-à-pair (P2P)** distribué mondialement.  
2. 📖 Une **blockchain** : registre immuable des transactions.  
3. ⚙️ Un **mécanisme de consensus Proof of Work (PoW)** assurant la sécurité.

---

## 📦 1. Structure d’un bloc

Chaque bloc contient les informations nécessaires à la vérification et à la continuité de la chaîne :

| Élément | Description |
|----------|--------------|
| **Version** | Indique la version du protocole. |
| **Hash du bloc précédent** | Lien vers le bloc précédent (assure la continuité). |
| **Merkle Root** | Racine cryptographique représentant toutes les transactions du bloc. |
| **Horodatage (timestamp)** | Date/heure de création du bloc. |
| **Bits (difficulty target)** | Niveau de difficulté du PoW. |
| **Nonce** | Valeur testée par les mineurs pour résoudre le PoW. |
| **Liste des transactions** | Toutes les transactions incluses dans le bloc. |

🧩 **Chaque bloc dépend du précédent** → une modification dans un bloc invaliderait tous les suivants.  
C’est le principe d’**immuabilité** de la blockchain Bitcoin.

---

## 💰 2. Le modèle UTXO (Unspent Transaction Output)

Contrairement à un compte bancaire qui garde un solde global,  
Bitcoin fonctionne avec des **UTXO** : des "sorties de transactions non dépensées".

Chaque transaction :
- **Dépense** des UTXO existants (*inputs*),
- Et **crée** de nouveaux UTXO (*outputs*).

### 🔄 Exemple simplifié :

- Alice possède un UTXO de **1 BTC**  
- Elle envoie **0.7 BTC** à Bob → crée une sortie de **0.7 BTC pour Bob**  
- Elle récupère **0.3 BTC** de “change” sur une nouvelle adresse à elle-même  

Ainsi, **les soldes n’existent pas directement** :  
ils sont calculés comme la somme des UTXO qu’un utilisateur peut dépenser.

---

### 🔐 Scripts et signatures

Chaque UTXO est verrouillé par un **locking script** (`scriptPubKey`) :
```bash
OP_DUP OP_HASH160 <PubKeyHash> OP_EQUALVERIFY OP_CHECKSIG

Pour le dépenser, le propriétaire doit fournir un unlocking script (scriptSig) :

<Signature> <PublicKey>

✅ Si la signature correspond à la clé publique du propriétaire → la transaction est valide.

⚡ Avantages du modèle UTXO

✅ Vérification parallèle possible → hautement scalable

🔏 Confidentialité accrue → nouvelles adresses à chaque transaction

🧮 Facilement traçable et vérifiable pour les nœuds

🧠 Base technique pour des extensions comme Lightning Network ou Taproot

🔐 3. Cryptographie et sécurité

Bitcoin repose sur deux primitives cryptographiques principales :

🧩 a) SHA-256

Une fonction de hachage cryptographique :

Produit une empreinte unique de 256 bits.

Utilisée pour :

Les hashs de transactions

La Merkle Root

Le hash du bloc

Propriétés :

Déterministe

Irréversible

Résistante aux collisions

✍️ b) ECDSA (Elliptic Curve Digital Signature Algorithm)

Bitcoin utilise la courbe elliptique secp256k1.

Chaque utilisateur possède :

Une clé privée (nombre aléatoire secret)

Une clé publique dérivée de cette clé

Une adresse Bitcoin dérivée du hash de la clé publique

Lorsqu’un utilisateur signe une transaction :

Le message (données de la transaction) est haché.

Ce hash est signé avec la clé privée.

La signature est vérifiée par tous les nœuds via la clé publique.

🛡️ Cela garantit :

L’authenticité (le propriétaire est bien l’émetteur)

L’intégrité (la transaction n’a pas été modifiée)

La non-répudiation

⚙️ 4. Proof of Work (PoW) et minage

Le Proof of Work est le mécanisme de consensus du réseau Bitcoin.
Il garantit que tous les nœuds s’accordent sur une seule version du registre.

🔨 Étapes du minage

Le mineur regroupe des transactions valides dans un bloc candidat.

Il calcule le hash du header du bloc.

Il modifie le nonce jusqu’à obtenir un hash inférieur à la cible de difficulté.

Une fois trouvé → il diffuse le bloc au réseau.

Les autres nœuds vérifient le bloc avant de l’ajouter à la blockchain.

🎁 Récompense du mineur

Block reward : création monétaire (actuellement 3.125 BTC depuis le halving de 2024).

Frais de transaction inclus dans le bloc.

💡 Tous les 210 000 blocs (~4 ans), la récompense est divisée par deux : c’est le Halving.

🧩 5. Ajustement de difficulté

Tous les 2016 blocs (~2 semaines), le réseau ajuste automatiquement la difficulté du PoW.

Si les blocs sont trouvés trop vite → difficulté augmente

S’ils sont trouvés trop lentement → difficulté diminue

🎯 Objectif : maintenir un rythme constant d’un bloc toutes les 10 minutes.

Ce mécanisme auto-régulateur permet à Bitcoin de s’adapter dynamiquement à la puissance de calcul du réseau.

💎 6. Politique monétaire et rareté

Bitcoin suit une politique monétaire programmée, transparente et prévisible.

Élément	Détail
Offre totale	21 millions de BTC
Bloc initial (Genesis)	Janvier 2009
Halving	Tous les 210 000 blocs (~4 ans)
Récompense actuelle (2025)	3.125 BTC par bloc
Dernier Bitcoin miné	Environ en 2140

⚖️ Cette rareté algorithmique crée une pression déflationniste et renforce le caractère de réserve de valeur du Bitcoin.

🔍 7. Rôle des nœuds

Les nœuds complets (full nodes) :

Vérifient chaque transaction et chaque bloc.

Maintiennent une copie complète de la blockchain.

Assurent l’intégrité du réseau sans autorité centrale.

Les mineurs, eux :

Sécurisent le réseau via la preuve de travail.

Proposent de nouveaux blocs.

Reçoivent les récompenses (block reward + frais).

🧠 8. Synthèse

Bitcoin combine trois technologies fondamentales :

Composant	Rôle
🔐 Cryptographie asymétrique	Sécurise la propriété des fonds
⚙️ Proof of Work	Assure le consensus et la résistance à la falsification
💰 Modèle UTXO	Structure les transactions et la traçabilité
