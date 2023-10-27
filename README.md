# robot.ai

## Table des matières

1. [Introduction](#introduction)
2. [Définitions](#définitions)
3. [Structure du fichier `robot.txt`](#structure-du-fichier)
4. [Limitations et responsabilités](#limitations-et-responsabilités)
5. [Paiement via la Plateforme Centralisée](#paiement-via-la-plateforme-centralisée)
6. [Notes finales](#notes-finales)

## Introduction

Cette convention établit les règles et directives pour l'adoption et l'utilisation d'une version augmentée du fichier `robot.txt`. Elle vise à déterminer les coûts associés au crawl de différentes sections d'un site web tout en utilisant une plateforme de paiement centralisée.

## Définitions

- **Crawl** : Action effectuée par un robot pour indexer ou récupérer des informations d'un site web.
- **Robot** : Programme ou script qui parcourt le web pour indexer des sites, récupérer des données, etc.

## Structure du fichier `robot.txt`

### Directives de base

- **User-agent**: Identifie spécifiquement le robot auquel la règle s'applique.
- **Crawl-cost**: Décrit le tarif associé au crawl d'une URL ou d'un ensemble d'URLs.
- **Crawl-Licence**: Correspond a la licence associé au crawl du document
- **Disallow**: Détermine les sections du site avec un coût spécifié.
- **Allow**: Permet le crawl de sections spécifiques du site à un tarif défini.
- **Payment-Platform**: URL de la plateforme centralisée pour les paiements.
- **Payment-Token**: Token unique reçu après l'enregistrement sur la plateforme de paiement.

### Hiérarchie des règles

Les règles définies pour des agents spécifiques l'emportent sur les règles définies pour tous les agents (`User-agent: *`).

## Limitations et responsabilités

1. **Limite de prix**: Le coût associé au crawl d'une URL ou d'un ensemble d'URLs ne doit pas dépasser 0.02 par page.
2. Il n'existe actuellement aucun mécanisme standard pour faire respecter cette convention.
3. Le respect de cette convention relève de la bonne foi des parties.
4. Le propriétaire du site est responsable de toute dispute ou question juridique découlant de l'utilisation de cette convention.

## Paiement via la Plateforme Centralisée

Les entreprises souhaitant être rémunérées pour le crawl de leur site adoptant cette convention doivent s'enregistrer sur la plateforme [permitbot.ai](https://www.permitbot.ai/). Après l'enregistrement, un token unique est délivré et doit être renseigné dans le `robot.txt` de leur site. 

Les entreprises qui souhaitent crawler doivent effectuer les paiements associés aux coûts de crawl directement via cette plateforme centralisée, en se basant sur le token fourni dans le `robot.txt`.

## Exemples d'utilisation du fichier `robot.txt`

### Exemple 1: Tarification de base pour tous les robots

```
User-agent: *
Crawl-cost: 0.01
Payment-Platform: https://www.permitbot.ai/
Payment-Token: abc123xyz789
```

Dans cet exemple, tous les robots (`User-agent: *`) qui souhaitent crawler le site doivent payer 0,01 par page qu'ils crawlent. Le paiement doit être effectué via la plateforme indiquée et le token renseigné est utilisé pour vérifier le paiement.

### Exemple 2: Tarification spécifique pour certains robots

```
User-agent: Googlebot
Crawl-cost: 0.005
Allow: /public/
Disallow: /private/
Payment-Platform: https://www.permitbot.ai/
Payment-Token: def456ghi012

User-agent: Bingbot
Crawl-cost: 0.02
Disallow: /sensitive-data/
Payment-Platform: https://www.permitbot.ai/
Payment-Token: jkl789mno345
```

Ici, il y a des règles spécifiques pour `Googlebot` et `Bingbot`. `Googlebot` a un coût de crawl plus faible et a accès à la section `/public/` mais pas à `/private/`. `Bingbot` a un coût de crawl plus élevé et n'a pas le droit d'accéder à `/sensitive-data/`.

### Exemple 3: Tarification mixte

```
User-agent: *
Crawl-cost: 0.01
Payment-Platform: https://www.permitbot.ai/
Payment-Token: pqr123stu456

User-agent: MySpecificBot
Crawl-cost: 0.015
Allow: /exclusive-content/
Payment-Platform: https://www.permitbot.ai/
Payment-Token: vwx789yza012
```

Dans cet exemple, il y a une tarification générale pour tous les robots et une specifique pour MySpecificBot. Ce dernier a un tarif légèrement plus élevé et a un accès exclusif à /exclusive-content/.

## Notes finales

1. **Sécurité**: Assurez-vous de bien protéger votre token et de ne le partager qu'avec des entités de confiance.
2. **Respect de la convention**: Le non-respect des directives du `crawl-pricing.txt` peut entraîner des conséquences juridiques ou d'autres mesures.
3. **Assistance**: Pour toute question ou assistance concernant la plateforme [permitbot.ai](https://www.permitbot.ai/), veuillez consulter la documentation officielle ou contacter le support.
