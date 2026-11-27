# Sujet — ZakFit

Résumé du brief et du cahier des charges. Les documents originaux font foi.

## Le besoin

Les utilisateurs d'apps fitness rencontrent 4 problèmes :

1. **Données éclatées** : changer de téléphone ou se déconnecter fait perdre l'historique.
2. **Suivi peu lisible** : pas de visualisation simple des progrès.
3. **Apps rigides** : régimes particuliers et objectifs personnels mal pris en charge.
4. **Sécurité** : peu de confiance dans le stockage des données de santé.

ZakFit y répond avec une base de données centralisée, un suivi des repas et des activités, des graphiques, des objectifs personnalisables et une authentification JWT.

**Cible** : du débutant au sportif confirmé.

## Contraintes techniques

- App en **SwiftUI**, architecture **MVVM**.
- API **RESTful** en **Vapor**, base **MySQL** relationnelle et **normalisée** (clés primaires et étrangères).
- **JWT** vérifié à chaque requête protégée ; token expiré = accès refusé.
- Mots de passe **hachés** (bcrypt) ; données sensibles stockées et transmises de façon sécurisée.
- **CORS** géré.
- Requêtes SQL optimisées.
- Optionnel : HTTPS, cache, réduction des appels API.

## Écrans exigés

| Écran | Contenu |
| --- | --- |
| Connexion / inscription | nom, prénom, email unique, mot de passe ≥ 8 caractères (+ confirmation) |
| Tableau de bord | calories consommées, activités, graphiques |
| Suivi des repas | type de repas, recherche d'aliments, quantité, aliment personnalisé ; repas du jour avec calories, macros et totaux |
| Suivi des activités | type, durée, calories (saisies ou estimées) ; historique filtrable (type, durée, période) et triable |
| Objectifs et paramètres | profil (taille, poids, régime, objectif), objectifs calories / macros / activité, mot de passe, déconnexion |

La déconnexion supprime le JWT côté app ; aucun appel serveur n'est nécessaire.

## Livrables

**Conception** : dictionnaire des données, MCD, MLD, MPD, diagramme de classes, diagramme de cas d'utilisation, maquette Figma.

**Base de données** : script SQL complet (tables + relations), tables remplies de données fictives.

**Backend** : API Vapor avec endpoints documentés, authentification JWT, Fluent + quelques requêtes SQL en dur, CORS.

**App iOS** : application fonctionnelle avec synchronisation complète des données, sur les 5 écrans ci-dessus.

## Critères d'évaluation

- **Fonctionnalité** : chaque écran fonctionne et est connecté à la base ; calculs (calories, objectifs) exacts et à jour en temps réel.
- **Qualité technique** : code propre, structuré, commenté ; bonnes pratiques Swift et Vapor.
- **Design** : interfaces ergonomiques, conformes à la maquette Figma.
- **Fiabilité** : pas de crash, réponses rapides.
- **Documentation** : livrables accompagnés d'une doc claire et complète.
- **Présentation et démonstration** des fonctionnalités : pas de soutenance orale, voir [`demo.md`](demo.md).
