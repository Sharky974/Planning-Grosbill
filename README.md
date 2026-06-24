# Planning Grosbill

Application de gestion de planning hebdomadaire pour magasin, en version Windows autonome (`.exe` portable, sans installation). Toutes les données restent en local sur le poste.

**Version actuelle : v1.3.0**

---

## Présentation

Planning Grosbill permet de construire le planning hebdomadaire de l'équipe d'un magasin, de vérifier automatiquement sa conformité (contrats, couverture, habilitations) et de produire des documents prêts à imprimer (planning et affiche horaires).

Depuis la version **1.2.0**, l'application intègre un assistant de configuration au premier lancement afin de préparer rapidement le planning selon le magasin, l'équipe et les horaires d'ouverture.

---

## Fonctionnalités

### Assistant de configuration initiale

Au premier lancement, un menu de configuration permet de préparer l'application avant d'accéder au planning :

- Choix du magasin via un **menu déroulant**.
- Liste des magasins Grosbill intégrée : Paris 13e, Paris 15e, Paris 16e, Montigny-lès-Cormeilles, Sainte-Geneviève-des-Bois, Plan de Campagne, Roncq, Villeneuve-d'Ascq, Lyon 3e, Saint-Priest et Rouen Barentin.
- Option **Autre magasin…** avec champ libre pour saisir un nom personnalisé.
- Création de l'équipe dès le démarrage : nom, volume horaire de contrat et statut **Employé confirmé**.
- Définition des jours d'ouverture et des créneaux matin / après-midi.
- Bouton **Démarrer le planning** pour valider la configuration et accéder à l'interface principale.

Un indicateur interne de configuration permet d'afficher cet assistant uniquement lorsque l'application n'a pas encore été paramétrée. Les anciennes données sauvegardées restent compatibles et ne déclenchent pas l'assistant par erreur.

### Tableau de bord

Quatre indicateurs se recalculent automatiquement à chaque modification :

- **Effectif** — nombre total d'employés, avec le détail actifs / absents.
- **Heures planifiées** — cumul des heures de toute l'équipe sur la semaine.
- **Conformité contrats** — nombre de contrats respectés sur le nombre d'actifs.
- **Alertes** — nombre de problèmes détectés, dont les bloquants.

### Gestion de l'équipe

- Ajout, suppression et réorganisation des employés (monter / descendre dans la liste).
- Pour chaque employé : nom, volume de contrat (en heures), jours de repos, statut **Employé confirmé**.
- Statut **Congé** ou **Absent** activable par employé (retiré des calculs d'heures).

### Saisie du planning

- Grille hebdomadaire (lundi au dimanche), un ou plusieurs créneaux par jour et par employé.
- Saisie des horaires au format libre `HH:MM` : on peut taper `14`, `1400`, `14h30`… la mise en forme se fait automatiquement.
- Calcul automatique du total d'heures par employé et de l'écart par rapport au contrat (en avance / en retard).

### Contrôles automatiques de conformité

Détectés et signalés en temps réel :

- horaires invalides (heure de fin avant l'heure de début) ;
- créneaux hors des horaires d'ouverture du magasin ;
- chevauchements de créneaux pour un même employé ;
- trous de couverture : créneaux où personne n'est présent en magasin ;
- **volume horaire non conforme au contrat** : un employé qui dépasse ou n'atteint pas son contrat hebdomadaire est signalé, de même qu'un employé sans aucune heure planifiée ;
- travail en solo non confirmé : un employé seul à l'ouverture ou à la fermeture sans statut **Employé confirmé**.

Les alertes sont graduées sur trois niveaux :

- **Avertissement** (orange) — écart à ajuster, jusqu'à 2 h de différence avec le contrat ;
- **Hors contrat / incohérence** (rouge) — écart de plus de 2 h, ou aucune heure planifiée ;
- **Bloquant** — personne seule non habilitée en magasin.

### Horaires d'ouverture du magasin

- Définition des jours d'ouverture et des plages horaires (matin / après-midi) pour chaque jour.
- Servent de référence pour tous les contrôles de cohérence du planning.
- Peuvent être initialisés directement depuis l'assistant de configuration.

### Exports / impression

- Export du planning en **PDF**, prêt à imprimer.
- **Affiche horaires** A4 paysage, avec logo Grosbill, prête à afficher en vitrine ou sur la porte. Regroupement automatique des jours ayant les mêmes horaires (ex. « DU MARDI AU SAMEDI »).

### Confort d'usage

- Thème clair / sombre au choix.
- Sauvegarde automatique locale après chaque modification (double stockage pour la robustesse).
- Compatibilité avec les données sauvegardées des versions précédentes.
- Réinitialisation possible pour relancer l'assistant de configuration et repartir proprement.

---

## Installation

Aucune installation requise. Téléchargez `Planning-Grosbill-portable.exe` et lancez-le directement. Les données sont conservées entre les lancements.

> Au premier lancement, Windows peut afficher un avertissement SmartScreen (éditeur inconnu) : cliquer sur **Informations complémentaires** puis **Exécuter quand même**.

---

## Avertissement

Ce logiciel n'est **pas** développé par le groupe Cybertek. Il s'agit d'un outil indépendant. Il n'utilise en aucun cas les logs ou données du système JAJA.

---

## Changelog

### v1.3.0

- **Alertes de conformité du volume horaire** : détection automatique des employés en **dépassement** ou en **déficit** par rapport à leur contrat hebdomadaire, ainsi que des employés **sans aucune heure planifiée**. Les écarts sont gradués — orange « à ajuster » (jusqu'à 2 h), rouge « hors contrat » (au-delà de 2 h)
- **Nettoyage du code** : retrait de fonctions de sauvegarde / restauration JSON qui n'étaient reliées à aucune action, et correction du libellé du bouton de réinitialisation
- **Bug Fix** : Correction de plusieurs bug rencontré lors de l'utilisation.

### v1.2.0

- **Assistant de configuration au premier lancement** : choix du magasin, création de l'équipe et définition des horaires d'ouverture avant d'accéder au planning.
- **Menu déroulant des magasins Grosbill** : intégration des 11 magasins fournis, avec une option **Autre magasin…** pour saisir un nom personnalisé.
- **Statut Employé confirmé** : remplacement du libellé « Autonomie » par **Employé confirmé** dans l'assistant et dans l'interface principale.
- **Persistance de la configuration** : ajout d'un indicateur interne permettant de ne plus afficher l'assistant une fois l'application configurée.
- **Compatibilité avec les anciennes sauvegardes** : les données existantes des versions précédentes sont considérées comme déjà configurées.
- **Correction de démarrage** : résolution de l'erreur `ReferenceError: can't access lexical declaration 'app' before initialization`.
- **Réinitialisation améliorée** : la réinitialisation permet de relancer l'assistant de configuration.

### v1.1.0

- **Saisie des horaires simplifiée** : champs en texte libre `HH:MM` avec mise en forme automatique, à la place de l'ancien sélecteur qui obligeait à modifier les heures et minutes séparément.
- **Affiche horaires PDF retravaillée** : les deux créneaux (matin / après-midi) sont désormais empilés et centrés proprement ; suppression de l'élément graphique parasite entre les deux lignes.
- **Logo Grosbill intégré** comme icône de l'application (barre des tâches, fenêtre et explorateur).
