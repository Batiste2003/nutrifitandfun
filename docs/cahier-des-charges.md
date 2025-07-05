# Cahier des charges – Refonte du site Nutri Fit & Fun

## 1. Objectifs

- Moderniser l’interface et l’expérience utilisateur (UI/UX)
- Optimiser la navigation et l’accessibilité sur tous supports (responsive)
- Mettre en avant l’offre, la personnalité de la coach et les témoignages (récupérés sur Google directement ?)
- Faciliter la prise de contact et la conversion
- Respecter les obligations légales (RGPD, mentions légales)
- Utiliser une stack moderne, économique et performante (Nuxt, Vue.js, Supabase, Tailwind CSS)

---

## 2. Pages et arborescence

```
/
├── accueil (landing moderne)
├── a-propos
├── tarifs
├── blog/
│   ├── banana-bread-au-maca
│   ├── easy-pancakes
│   └── miracle-morning
├── contact
├── inscription (signup)
├── connexion (login)
├── dashboard (user)
├── admin (dashboard admin)
├── reservation
├── paiement
├── messagerie
└── politique-de-confidentialite
```

### Détail des pages

#### 2.1. Accueil (`/accueil`)
- Hero section (titre, sous-titre, visuel fort)
- Présentation rapide de l’offre
- Mise en avant des témoignages (import Google possible)
- CTA principal ("Me contacter" ou "Découvrir l’offre")
- Accès rapide aux autres pages

#### 2.2. Page d’accueil classique (`/`)
- Présentation synthétique du site et de la coach
- Mise en avant des offres clés
- CTA vers contact ou découverte des services

#### 2.3. À propos (`/a-propos`)
- Présentation détaillée de Lucie (parcours, valeurs, expertise)
- Photo(s) professionnelle(s)
- Approche et philosophie

#### 2.4. Tarifs (`/tarifs`)
- Grille tarifaire claire (coaching individuel/groupe, nutrition, sport, suivi)
- Explications des formules
- CTA vers contact ou prise de rendez-vous

#### 2.5. Blog (`/blog`)
- Liste d’articles (image, titre, date, extrait, bouton "Lire la suite")
- Pagination ou chargement progressif
- Filtres ou catégories (optionnel)
- Page article détaillée
- Système de réactions/commentaires pour les utilisateurs connectés

#### 2.6. Contact (`/contact`)
- Formulaire de contact ergonomique (nom, email, message, RGPD)
- Coordonnées (email, téléphone)
- Liens réseaux sociaux
- Carte (optionnel)

#### 2.7. Inscription (`/inscription`)
- Formulaire d’inscription (email/password, Apple, Google, Microsoft)
- Validation email

#### 2.8. Connexion (`/connexion`)
- Formulaire de connexion (email/password, Apple, Google, Microsoft)

#### 2.9. Dashboard utilisateur (`/dashboard`)
- Suivi coaching, réservations, messagerie, profil

#### 2.10. Dashboard admin (`/admin`)
- Gestion coachings, utilisateurs, KPIs

#### 2.11. Réservation (`/reservation`)
- Calendrier connecté à Google Agenda (Lucie)
- Réservation de créneaux, validation/refus

#### 2.12. Paiement (`/paiement`)
- Paiement en ligne sécurisé (Stripe ou équivalent)

#### 2.13. Messagerie (`/messagerie`)
- Messagerie temps réel, indicateur de présence

#### 2.14. Politique de confidentialité (`/politique-de-confidentialite`)
- Informations RGPD, cookies, gestion des données personnelles

#### 2.15. Authentification & Profils
- Pages d’inscription et de connexion (email/password, Apple, Google, Microsoft)
- Gestion des rôles (admin, user)
- Création et gestion de profil utilisateur
- Tableau de bord utilisateur (suivi coaching, réservations, messagerie)
- Tableau de bord admin (gestion coachings, KPIs, gestion utilisateurs)

#### 2.16. Réservation & Paiement
- Système de calendrier connecté à Google Agenda (Lucie)
- Réservation de créneaux de coaching par les utilisateurs
- Validation ou refus des réservations par Lucie
- Système de paiement en ligne pour les coachings (Stripe ou équivalent, gestion via store Pinia ou autre)

#### 2.17. Messagerie
- Messagerie temps réel (websocket) entre utilisateurs et Lucie
- Indicateur de présence (en ligne/hors ligne)

#### 2.18. Notifications & Emails
- Envoi d’un email de confirmation d’inscription à Lucie et à l’utilisateur
- Notifications pour les réservations, messages, etc.

---

## 3. Composants réutilisables

- **Header** : Logo, navigation desktop/mobile (menu burger)
- **Footer** : Liens de navigation, réseaux sociaux, mentions légales, copyright
- **Hero Section** : Titre, sous-titre, visuel, CTA
- **Testimonials** : Slider ou liste, photo, nom, texte, note
- **Article Preview** : Image, titre, date, extrait, bouton
- **Blog Grid** : Grille d’articles
- **CTA Buttons** : Boutons stylisés, récurrents
- **Formulaire de contact** : Validation, accessibilité, feedback utilisateur
- **Calendrier de réservation**
- **Composants dashboard (admin/user)**
- **Messagerie temps réel**
- **Notifications**

---

## 4. Fonctionnalités attendues

- Site responsive (mobile, tablette, desktop)
- Navigation fluide (menu sticky, transitions douces)
- Accessibilité (contrastes, navigation clavier, ARIA)
- SEO optimisé (balises, performance, sitemap, meta)
- Intégration réseaux sociaux (liens, icônes, partage)
- Gestion des avis clients (slider, import Google possible)
- Système de blog performant (stockage des articles dans Supabase ou fichiers markdown)
- RGPD : gestion cookies, consentement, mentions légales
- Authentification multi-fournisseurs (email/password, Apple, Google, Microsoft)
- Gestion des rôles (admin/user)
- Réservation de coaching avec synchronisation Google Agenda
- Paiement en ligne sécurisé (Stripe ou équivalent)
- Dashboards personnalisés (admin et user)
- Messagerie temps réel avec indicateur de présence
- Notifications et emails automatiques

---

## 5. Stack technique retenue

- **Framework fullstack** : Nuxt (Vue.js)
- **Base de données** : Supabase (PostgreSQL, Auth, API REST, Realtime)
- **UI** : Tailwind CSS
- **Déploiement** : Vercel, Netlify ou équivalent
- **Paiement** : Stripe (intégration possible avec Pinia pour le store)
- **Messagerie** : Websocket (via Supabase Realtime ou service dédié)
- **Calendrier** : Intégration Google Calendar API
- **Formulaire** : gestion via API Supabase ou service externe (Formspree, EmailJS…)
- **TypeScript** : optionnel, le projet sera en JavaScript natif sauf besoin spécifique

---

## 6. Contenus à prévoir

- Textes pour chaque page (présentation, offres, articles…)
- Photos professionnelles (coach, ambiance, témoignages)
- Illustrations/icônes pour l’UI
- Témoignages clients (texte, photo, note)
- Mentions légales, politique de confidentialité

---

## 7. Livrables

- Code source du site (GitHub)
- Documentation d’administration (ajout articles, gestion contenu via Supabase)
- Procédure de déploiement

---