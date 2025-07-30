
# Gestion de factures PDF

## 🎯 Objectif

Automatiser le traitement des factures fournisseurs reçues, enregistrées dans un dossier local, pour en faciliter le classement par fournisseur.

## 🏢 Contexte professionnel

Le service comptabilité d’une PME reçois Chaque semaine des factures fournisseurs au format PDF par email. Ces pièces jointes sont sauvegardées dans le dossier C:\Factures\A_traiter.

## ⚙️ Fonctionnement de l’automatisation

Le robot Power Automate Desktop effectue les actions suivantes :

  ### Parcours de fichiers
    
    Il Parcourt tous les fichiers PDF présents dans C:\Factures\A_traiter.

  ### Lecture et extraction
    Lit le nom de chaque fichier de type :
    FACTURE_FournisseurNom_202507.pdf
    → Extraction dynamique du nom du fournisseur (FournisseurNom).

  ### Renommage
    Renomme le fichier sous le format :
    FournisseurNom_YYYY-MM-DD.pdf (en utilisant la date du jour).

  ### Création du dossier fournisseur
   
    Vérifie si le dossier C:\Factures\Archives\FournisseurNom existe, et le crée si nécessaire.

  ### Déplacement
    Déplace le fichier renommé vers C:\Factures\Archives\FournisseurNom.

## 🔧 Étapes de conception dans Power Automate Desktop

  1. Initialisation des variables

    DossierSource = C:\Factures\A_traiter

    DossierDestination = C:\Factures\Archives

    DateDuJour = Format datetime → dd-MM-yyyy à partir de l'action "Obtenir la date et l'heure actuelle"

 2. Parcourir les fichiers PDF

    Action : Obtenir les fichiers dans un dossier

    Filtre : *.pdf

    Stocker la liste des fichiers dans Fichiers

3. Boucle Pour chaque fichier dans Fichiers

  Dans la boucle :
  a. Extraire le nom du fichier

    Action : Obtenir le nom du fichier sans l'extension
    Variable : NomFichierSansExtension

  b. Extraire dynamiquement le nom du fournisseur

    Action : Fractionner texte
    Chaîne : NomFichier, Délimiteur : _
    → Résultat : ListeElements

        Fournisseur = ListeElements[1]

  c. Renommer le fichier

    Nouveau nom = Fournisseur + "_" + DateDuJour

d. Créer le sous-dossier fournisseur

    Chemin complet = DossierDestination + "\" + FournisseurNom

    Action : Créer un dossier (avec vérification de l'existence)

e. Déplacer le fichier renommé

    Action : Déplacer le fichier

    Source : fichier actuel

    Destination : DossierDestination\Fournisseur\NouveauNom

🧪 Exemple
Fichier d’origine :

C:\Factures\A_traiter\FACTURE_Auchan_202507.pdf

Fichier renommé :

C:\Factures\Archives\Auchan\Auchan_2025-07-30.pdf

✅ Compétences mobilisées

    Manipulation de fichiers et dossiers

    Extraction dynamique avec Split

    Création de variables

    Utilisation des dates

    Boucles et conditions


<img width="1455" height="803" alt="Image" src="https://github.com/user-attachments/assets/05acb4e1-5ed2-4187-bea0-81f6c2c67127" />

<img width="1450" height="500" alt="Image" src="https://github.com/user-attachments/assets/415affa1-340f-417a-99bd-608bcb5f69ed" />
