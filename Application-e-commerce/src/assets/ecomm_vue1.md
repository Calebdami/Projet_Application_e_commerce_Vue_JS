# 🛒 TP Vue.js — Application e-commerce

## 🗂️ Structure attendue du projet

```
src/
│
├── router/
│   └── index.js
│
├── components/
│   ├── ProductCard.vue
│   ├── CartItem.vue
│   └── PaymentForm.vue
│
├── views/
│   ├── HomeView.vue
│   ├── ProductsView.vue
│   ├── ProductDetailsView.vue
│   └── CartView.vue
│
├── App.vue
└── main.js
```

---

## 🧭 Pages à réaliser (avec Vue Router)

### 1️⃣ Page d’accueil — `HomeView`

**Rôle :**

* Présenter la boutique
* Contenir un bouton ou lien vers la page produits

**Fonctionnalités attendues :**

* Texte de bienvenue
* Bouton “Voir les produits”

---

### 2️⃣ Page liste des produits — `ProductsView`

**Rôle :**

* Afficher tous les produits disponibles

**Contraintes :**

* Chaque produit est affiché via un **composant `ProductCard`**

---

### 3️⃣ Page détails d’un produit — `ProductDetailsView`

### 4️⃣ Page panier — `CartView`


## 🧩 Composants obligatoires

### 🧩 `ProductCard.vue`

Utilisé dans :

* Page liste des produits

---

### 🧩 `CartItem.vue`

Utilisé dans :

* Page panier
---

### 🧩 `PaymentForm.vue`

Utilisé dans :

* Page panier

Rôle :

* Simuler un paiement

Champs requis :

* Nom du client
* Numéro de carte (fictif)
* Bouton “Payer”

Comportement :

* Afficher un message “Paiement effectué avec succès”

⚠️ **Aucune vraie logique bancaire**

---

## 🛒 Gestion du panier

Le panier doit :

* Être stocké dans un **state global simple** (ex : `reactive()` dans `App.vue`)
* Être passé aux composants via `props`
* Être modifié via des événements (`emit`)

Fonctionnalités obligatoires :

* Ajouter un produit
* Afficher les produits du panier
* Calculer le total
* Supprimer un produit

---