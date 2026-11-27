# ZakFit

Application iOS de suivi nutrition et activité physique, avec une API qui centralise les données pour les retrouver sur n'importe quel appareil.

Projet individuel d'ECF — titre CDA, Advanced Apple Foundation Program (Simplon).
Durée : 3 semaines · rendu le **11 décembre 2026**.

## Aperçu

<!-- Teaser de 15 à 30 s : connexion → tableau de bord → ajout d'un repas → le graphique se met à jour.
     Remplacer par la vidéo glissée dans l'éditeur GitHub, ou par docs/assets/teaser.gif -->
![Teaser ZakFit](docs/assets/teaser.gif)

▶️ Démo complète : [`docs/demo.md`](docs/demo.md)

## Avant de commencer

Lire dans cet ordre :

1. [`docs/sujet.md`](docs/sujet.md) — le sujet et le cahier des charges, résumés
2. [`docs/perimetre.md`](docs/perimetre.md) — ce qui est obligatoire, ce qui est optionnel, ce qui est retenu
3. [`docs/modelisation/`](docs/modelisation/) — dictionnaire des données, MCD, MLD, MPD, diagrammes UML
4. [`docs/design/`](docs/design/) — maquettes des écrans
5. [`docs/demo.md`](docs/demo.md) — la démonstration complète, écran par écran

## Stack

| Couche           | Techno                                                                    |
| ---------------- | ------------------------------------------------------------------------- |
| App iOS          | SwiftUI, architecture MVVM, Swift Charts                                  |
| API              | Vapor (REST), Fluent + quelques requêtes SQL en dur (SQLKit)              |
| Base de données  | MySQL                                                                     |
| Authentification | JWT, mots de passe hachés en bcrypt                                       |
| Conception       | Merise (DD, MCD, MLD, MPD), UML (classes, cas d'utilisation), Figma       |
| Tests            | XCTVapor (calculs et API côté Vapor, validation des formulaires côté app) |

## Structure du dépôt

```
zakfit/
├── README.md
├── docs/
│   ├── modelisation/    
│   ├── design/           
│   ├── assets/           
│   ├── sujet.md
│   ├── perimetre.md
│   └── demo.md
├── database/             # schema.sql + seed.sql
├── backend/              # API Vapor
└── ios/                  # app SwiftUI
```

## Lancer le projet


Prérequis prévus : Xcode, Swift, MySQL.

```bash
# 1. API + base de données (MySQL lancé en local)
cp backend/.env.example backend/.env   # renseigner les secrets
cd backend
swift run App migrate                  # crée les tables
mysql -u <utilisateur> -p zakfit < ../database/seed.sql   # données de test
swift run

# 2. App iOS
open ios/ZakFit.xcodeproj
```