# BIBINE

Application de gestion de planning hebdomadaire pour magasin, en version Windows autonome (`.exe` portable, sans installation). Toutes les données restent en local sur le poste.

**Version actuelle : v2.1.3**

---

## Présentation

BIBINE permet de construire le planning hebdomadaire de l'équipe d'un magasin, de vérifier automatiquement sa conformité (contrats, couverture, habilitations) et de produire des documents prêts à imprimer (planning et affiche horaires). L'enseigne (Grosbill ou Cybertek) se choisit à l'intérieur de l'application.

Depuis la version **1.2.0**, l'application intègre un assistant de configuration au premier lancement afin de préparer rapidement le planning selon le magasin, l'équipe et les horaires d'ouverture.

---

## Fonctionnalités

### Assistant de configuration initiale

Au premier lancement, un menu de configuration permet de préparer l'application avant d'accéder au planning :

- Choix de l'**enseigne** via deux onglets : **Grosbill** ou **Cybertek**. L'application adopte alors automatiquement le logo, la couleur d'accent et la liste de magasins de l'enseigne sélectionnée.
- Choix du magasin via un **menu déroulant** adapté à l'enseigne.
- Magasins **Grosbill** : Paris 13e, Paris 15e, Paris 16e, Montigny-lès-Cormeilles, Sainte-Geneviève-des-Bois, Plan de Campagne, Roncq, Villeneuve-d'Ascq, Lyon 3e, Saint-Priest, Rouen Barentin.
- Magasins **Cybertek** : Agen, Anglet, Angoulins, Bègles, Bordeaux-Lac, Brest, Labège, Mérignac, Montauban, Nantes, Paris 2, Pau, Perpignan, Portet, St-Nazaire, Toulon, Toulouse-Nord.
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
- **Affiche horaires** A4 paysage, avec logo Grosbill/Cybertek, prête à afficher en vitrine ou sur la porte. Regroupement automatique des jours ayant les mêmes horaires (ex. « DU MARDI AU SAMEDI »).

### Confort d'usage

- Thème clair / sombre au choix.
- Sauvegarde automatique locale après chaque modification (double stockage pour la robustesse).
- Compatibilité avec les données sauvegardées des versions précédentes.
- Réinitialisation possible pour relancer l'assistant de configuration et repartir proprement.

---

## Installation

Aucune installation requise. Téléchargez `BIBINE-portable.exe` et lancez-le directement. Les données sont conservées entre les lancements.

> Au premier lancement, Windows peut afficher un avertissement SmartScreen (éditeur inconnu) : cliquer sur **Informations complémentaires** puis **Exécuter quand même**.

---

## Avertissement

Ce logiciel n'est **pas** développé par le groupe Cybertek. Il s'agit d'un outil indépendant. Il n'utilise en aucun cas les logs ou données du système JAJA.

---

## Changelog

### v2.1.3

- **Nouveau nom : Bibine - Planning Manager** (anciennement « Planning Grosbill »). Le renommage est appliqué partout : titre de la fenêtre, icône d'application, `README`, workflow de build, `package.json` (`name`, `productName`, `appId`) et nom de l'exécutable portable (`BIBINE-portable.exe`). Les enseignes **Grosbill** et **Cybertek** restent sélectionnables à l'intérieur de l'application (logo, couleur d'accent et liste de magasins) — ce sont des marques internes, distinctes du nom de l'application.
- **Nouveau logo d'application** : icône dédiée, utilisée comme favicon de l'application et comme icône de l'exécutable Windows (`build/icon.ico`, multi-tailles 16→256 px).
- **`package.json` remis à jour** : version `1.2.0` → `2.1.0`, `productName` = **Bibine - Planning Manager**, `appId` = `com.bibine.app`, `artifactName` = `BIBINE-portable.exe`.
- **Workflow GitHub (`build.yml`)** : artifact renommé `Planning-Grosbill-portable` → `BIBINE-portable`.

### v2.0.1

- **Choix de l'enseigne au démarrage** : deux onglets **Grosbill** / **Cybertek** dans l'assistant de configuration. Selon l'enseigne retenue, l'application bascule automatiquement le **logo**, la **couleur d'accent** et la **liste des magasins** — y compris dans l'export PDF du planning et l'affiche horaires.
- **17 magasins Cybertek** intégrés à la liste déroulante (en plus des magasins Grosbill).
- **Thème couleur par enseigne** : accent rouge Grosbill (`#D81E2C`) ou jaune Cybertek (`#FFCF00`, avec texte foncé sur les aplats, comme l'identité Cybertek). Les alertes et erreurs restent en rouge dans les deux cas pour rester lisibles. Géré via une variable de thème unique appliquée à toute l'interface.
- **Mode sombre généralisé** : le thème sombre s'applique aussi à l'écran de configuration (bouton clair / sombre dédié), et le logo Cybertek (noir) passe automatiquement en blanc sur fond sombre pour rester lisible.
- **Icône d'application** : logo dédié (calendrier + circuit + validation) utilisé comme favicon de l'application.
- **Champ libre « Description »** dans l'en-tête (anciennement la période), éditable et sauvegardé.

### v1.3.0

- **Alertes de conformité du volume horaire** : détection automatique des employés en **dépassement** ou en **déficit** par rapport à leur contrat hebdomadaire, ainsi que des employés **sans aucune heure planifiée**. Les écarts sont gradués — orange « à ajuster » (jusqu'à 2 h), rouge « hors contrat » (au-delà de 2 h).
- **Démarrage épuré** : suppression des employés d'exemple présents dans le code ; l'application s'ouvre désormais directement sur l'assistant de configuration.
- **Nettoyage du code** : retrait de fonctions de sauvegarde / restauration JSON qui n'étaient reliées à aucune action, et correction du libellé du bouton de réinitialisation.
- **Publication GitHub** : workflow de build mis à jour pour générer automatiquement une *Release* avec l'`.exe` lors d'un tag de version.

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
