# GateSys — Système de Gestion Stargate

GateSys est une application de bureau Windows Forms développée en C# avec .NET Framework 4.8.

L'application s'appuie sur une base de données locale SQLite (`Stargate.db`) pour centraliser les données sur les planètes, les espèces extraterrestres (alliées ou ennemies), les membres des équipes d'exploration, le budget et le journal des événements de chaque mission.

<p align="center">
  <img src="images/tableauBord.png" alt="Tableau de bord GateSys" width="600" />
</p>

---

## Fonctionnalités

GateSys offre une interface utilisateur immersive sur le thème de Stargate, dotée d'une charte graphique personnalisée (tons sombres, typographie *Saira Condensed*, boutons réactifs au survol). Ses fonctionnalités principales sont :

### 1. Gestion des Missions & Équipages
* **Création de Mission** : Formulaire dédié permettant de définir la destination (planète), la date de départ, la date de retour estimée, le budget alloué en crédits ($DG), et une feuille de route détaillée.
* **Sécurisation des accès** : La création de missions est protégée par un formulaire d'authentification (`frmLogin`) intégrant la validation sécurisée par mot de passe.
* **Constitution de l'Équipage** : Affectation des membres à la mission (militaires et scientifiques), avec distinction automatique des rôles (chef de mission/capitaine).
* **Objectifs de Capture** : Définition d'objectifs précis de capture d'espèces hostiles sur les planètes d'arrivée.

<p align="center">
  <img src="images/Mission.png" alt="Gestion des Missions" width="500" />
</p>

### 2. Suivi et Journal de Bord des Missions
* **Fiche de Mission Détaillée** : Vue d'ensemble affichant le statut de la mission (En cours ou Terminée), l'équipage affecté, les objectifs de capture, le budget initial et le budget restant calculé en temps réel après déduction des dépenses.
* **Journal des Événements** : Enregistrement chronologique et consultation étape par étape des événements survenus pendant l'expédition.
* **Suivi Financier** : Enregistrement des dépenses de la mission classées par catégorie (équipement, logistique, imprévus, etc.).
* **Rapport des Captures** : Déclaration des spécimens extraterrestres capturés au cours de la mission pour valider les objectifs.
* **Gestion des Informateurs** : Suivi des versements financiers (soudoiements) effectués aux indics locaux pour obtenir des renseignements clés.

### 3. Encyclopédie Stellaire & Diplomatie
* **Base de Données des Planètes** : Explorateur de l'univers connu affichant les caractéristiques de chaque planète (température moyenne, gravité, présence de la ressource stratégique *DataBaz* et statut opérationnel de sa porte des étoiles).
* **Base de Données des Espèces** : Répertoire complet des peuples extraterrestres (Aliens) répertoriés selon leur type de relation (Alliés, Ennemis, Neutres) et leurs caractéristiques physiques (couleur de peau, degré de bienveillance ou instruments de musique préférés).
* **Demandes de Négociation** : Module d'échange de ressources permettant de négocier des quantités de *DataBaz* auprès des factions alliées rencontrées.

<p align="center">
  <img src="images/Planete.png" alt="Encyclopédie Stellaire et Planètes" width="500" />
</p>

### 4. Module de Statistiques Avancées
* **Statistiques Financières** : Graphiques d'analyse comparative montrant le budget alloué par rapport aux dépenses réelles engagées sur chaque planète.
* **Missions par Planète** : Représentation visuelle de la fréquence des explorations par secteur.
* **Suivi des Coopérations** : Outil permettant de visualiser avec quels collègues un membre d'équipage spécifique a déjà collaboré.
* **Analyse des Informateurs** : Classement et totalisation des récompenses financières versées aux informateurs par mission.

---

## Installation et Configuration

Pour exécuter et compiler ce projet en local, suivez les instructions ci-dessous :

### Prérequis
* **Système d'exploitation** : Windows 10/11 (ou Linux/macOS avec Mono/Wine pour exécuter le binaire).
* **Environnement de développement** : [Visual Studio](https://visualstudio.microsoft.com/) (version 2019 ou ultérieure recommandée) ou [JetBrains Rider](https://www.jetbrains.com/rider/).
* **Framework** : .NET Framework 4.8.
* **Gestionnaire de paquets** : NuGet.

### Instructions d'installation
1. **Cloner le dépôt** :
   ```bash
   git clone https://github.com/votre-compte/GateSys.git
   cd GateSys
   ```
2. **Restaurer les packages NuGet** :
   Ouvrez la solution `saeStargateTUAILLON_LONGO_YURTSEBEN.sln` dans votre IDE. Les paquets requis (comme `System.Data.SQLite.Core` pour la base de données, `BCrypt.Net-Core` pour la sécurité et `iTextSharp` pour les exports) seront restaurés automatiquement lors du premier build. Vous pouvez également exécuter la commande suivante dans le terminal :
   ```bash
   dotnet restore saeStargateTUAILLON_LONGO_YURTSEBEN.sln
   ```
3. **Placer la Base de Données SQLite** :
   Assurez-vous que le fichier de base de données SQLite nommé **`Stargate.db`** est présent dans le répertoire d'exécution de l'application (c'est-à-dire dans le dossier de compilation de sortie, typiquement `bin/Debug/` ou `bin/Release/`), au même niveau que le fichier exécutable `.exe`.
4. **Compiler et Exécuter** :
   Générez la solution (Build) et lancez l'exécution (`F5` sous Visual Studio).

---

## Architecture Technique & Technologies

* **Langage & Framework** : C# 8.0, Windows Forms (.NET Framework 4.8)
* **Base de données** : SQLite (via la bibliothèque `System.Data.SQLite`). La connexion est gérée sous forme de *Singleton* via la classe [Connexion.cs](file:///home/nexxo/GateSys/Connexion.cs) pour assurer l'unicité et la fermeture propre des accès à la base de données.
* **Sécurité** : Hachage des mots de passe avec BCrypt pour l'authentification.
* **Mise en page & Style** : Utilisation d'un moteur de style personnalisé dynamique ([Style.cs](file:///home/nexxo/GateSys/Style.cs)) qui applique récursivement la police d'écriture et les palettes de couleurs thématiques de l'univers Stargate à tous les contrôles graphiques.
