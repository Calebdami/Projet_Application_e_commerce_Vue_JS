**Quoi afficher exactement** :

# 🧩 1. Carte produit (ProductCard)

👉 Utilisée sur la **page de listing des produits**

L’objectif ici est :
**donner envie + info rapide + action**

### 📦 Données DummyJSON utilisées

(API : `/products`)

Champs principaux :

* `thumbnail`
* `title`
* `price`
* `discountPercentage`
* `rating`
* `brand`
* `id`

---

### 🖼️ Contenu à afficher sur une carte produit

#### Obligatoire

* **Image du produit**

  * `thumbnail`
* **Nom du produit**

  * `title`
* **Prix**

  * `price`
* **Note**

  * `rating` (ex : ⭐ 4.5)

### 🎯 Actions sur la carte

* Bouton **“Voir détails”**
* Bouton **“Ajouter au panier”**
---

# 🧩 2. Page détail produit (ProductDetailsView)

### 📦 Données DummyJSON utilisées

Champs importants :

* `images`
* `title`
* `description`
* `price`
* `discountPercentage`
* `rating`
* `stock`
* `brand`
* `category`

---

### 🖼️ Contenu à afficher sur la page détail

#### Informations principales

* **Galerie d’images**

  * `images[]`
* **Nom du produit**

  * `title`
* **Description**

  * `description`
* **Prix**

  * `price`
* **Réduction**

  * `discountPercentage`
* **Note**

  * `rating`

#### Informations secondaires

* **Marque**

  * `brand`
* **Catégorie**

  * `category`
* **Stock disponible**

  * `stock`

---

### 🎯 Actions disponibles

* Bouton **“Ajouter au panier”**
* Bouton **“Retour aux produits”**

---

# 🛒 3. Page panier (CartView)

👉 Contient la **liste du panier + paiement simulé**

---

## 🧩 Informations affichées dans le panier

Pour chaque produit ajouté :

* Image (`thumbnail`)
* Nom (`title`)
* Prix unitaire (`price`)
* Quantité
* Sous-total (`price × quantity`)
* Bouton supprimer

En bas :

* **Total général du panier**

---

# 💳 4. Composant Paiement (PaymentForm)

👉 Paiement **100 % simulé**
👉 Aucun appel API

---

### 📄 Champs du formulaire

* Nom du client
* Numéro de carte (fictif)
* Date d’expiration
* CVV (fictif)

---

### 🎯 Comportement attendu

* Bouton **“Payer”**
* Vérification simple :

  * champs non vides
  * panier non vide
* Affichage d’un message :

  * ✅ *“Paiement effectué avec succès”*
* Réinitialisation du panier après paiement

---

# 🧠 Récapitulatif rapide

| Élément       | Objectif                   |
| ------------- | -------------------------- |
| Carte produit | Découverte + action rapide |
| Page détail   | Information complète       |
| Panier        | Récap achat                |
| Paiement      | Simulation UX              |
