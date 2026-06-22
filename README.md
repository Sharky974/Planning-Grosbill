# Planning Grosbill

Application de gestion de planning hebdomadaire pour magasin, en version Windows autonome (`.exe` portable, sans installation). Toutes les données restent en local sur le poste.

**Version actuelle : v1.1.0**

---

## Présentation

Planning Grosbill permet de construire le planning hebdomadaire de l'équipe d'un magasin, de vérifier automatiquement sa conformité (contrats, couverture, habilitations) et de produire des documents prêts à imprimer (planning et affiche horaires).

---

## Fonctionnalités

### Tableau de bord

Quatre indicateurs se recalculent automatiquement à chaque modification :

- **Effectif** — nombre total d'employés, avec le détail actifs / absents.
- **Heures planifiées** — cumul des heures de toute l'équipe sur la semaine.
- **Conformité contrats** — nombre de contrats respectés sur le nombre d'actifs.
- **Alertes** — nombre de problèmes détectés, dont les bloquants.

### Gestion de l'équipe

- Ajout, suppression et réorganisation des employés (monter / descendre dans la liste).
- Pour chaque employé : nom, volume de contrat (en heures), jours de repos, habilitation au travail en autonomie.
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
- travail en solo non habilité : un employé seul à l'ouverture ou à la fermeture sans habilitation autonomie.

Les alertes bloquantes sont distinguées des simples avertissements.

### Horaires d'ouverture du magasin

- Définition des jours d'ouverture et des plages horaires (matin / après-midi) pour chaque jour.
- Servent de référence pour tous les contrôles de cohérence du planning.

### Exports / impression

- Export du planning en **PDF**, prêt à imprimer.
- **Affiche horaires** A4 paysage, avec logo Grosbill, prête à afficher en vitrine ou sur la porte. Regroupement automatique des jours ayant les mêmes horaires (ex. « DU MARDI AU SAMEDI »).

### Confort d'usage

- Thème clair / sombre au choix.
- Sauvegarde automatique locale après chaque modification (double stockage pour la robustesse).
- Réinitialisation possible pour repartir de l'exemple de départ.

---

## Installation

Aucune installation requise. Téléchargez `Planning-Grosbill-portable.exe` et lancez-le directement. Les données sont conservées entre les lancements.

> Au premier lancement, Windows peut afficher un avertissement SmartScreen (éditeur inconnu) : cliquer sur **Informations complémentaires** puis **Exécuter quand même**.

---

## Avertissement

Ce logiciel n'est **pas** développé par le groupe Cybertek. Il s'agit d'un outil indépendant. Il n'utilise en aucun cas les logs ou données du système JAJA.

---

## Changelog

### v1.1.0

- **Saisie des horaires simplifiée** : champs en texte libre `HH:MM` avec mise en forme automatique, à la place de l'ancien sélecteur qui obligeait à modifier les heures et minutes séparément.
- **Affiche horaires PDF retravaillée** : les deux créneaux (matin / après-midi) sont désormais empilés et centrés proprement ; suppression de l'élément graphique parasite entre les deux lignes.
- **Logo Grosbill intégré** comme icône de l'application (barre des tâches, fenêtre et explorateur).
