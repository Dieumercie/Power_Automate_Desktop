# 📦 Power Automate Desktop – Enregistrement de commandes fournisseurs (.txt ➜ SQL Server)

## 🎯 Objectif

Automatiser le traitement des commandes fournisseurs reçues par e-mail au format .txt, en extrayant les informations et en les enregistrant dans une base de données SQL Server.

### 🏢 Contexte professionnel fictif

Tu travailles dans une entreprise qui reçoit régulièrement des commandes fournisseurs par e-mail. Les fichiers .txt en pièce jointe sont sauvegardés automatiquement.
Tu dois extraire les informations contenues dans ces fichiers et les enregistrer dans une table Commandes_fournisseurs en base de données.
🧪 Exemple de fichier .txt

Nom_Fournisseur : Staples
Article : Souris optique
Quantité : 15
Priorité : Moyenne

🗃️ Table cible en base SQL Server : Commandes_fournisseurs
ID	Nom_Fournisseur	Article	Quantité	Date_de_Reception	Priorité

    💡 La date de réception est automatiquement récupérée depuis la propriété de création du fichier (.CreationTime).

🔧 Étapes automatisées dans le flux PAD
1. Connexion à SQL Server

    Ouverture de la connexion via un Provider=MSOLEDBSQL.1 avec sécurité intégrée

    Création de la base de données Commandes si elle n'existe pas

     Création de la base de donnéesde et de la table Commandes_fournisseurs

2. Lancer Outlook & récupérer les e-mails

    Lancement d’Outlook

    Récupération des e-mails non lus

    Enregistrer les pièces jointes dans un dossier

3. Récupération des fichiers .txt

    Dossier utilisé :
    D:\perso\Mes    projets\PowerAutomateDesktop\Gestions_Commandes\PJ\

    Filtrage des fichiers avec l’extension .txt

4. Extraction des données

    Boucle For each Fichier :

        Lecture du contenu du fichier .txt

        Stockage de la date de réception avec .CreationTime

        Fractionnement ligne par ligne du contenu

    Boucle For each ligne du fichier :

        Si la ligne contient :, on recadre le texte (extraction après :)

        Ajout des champs extraits à une liste Data

        Ajout également de la Date_de_Reception à la liste

5. Insertion dans SQL Server

    Boucle While avec incrémentation de l’index de 4 en 4 (1 commande = 4 champs) :

        Insertion dans la table Commandes_fournisseurs avec la requête :

        INSERT INTO Commandes_fournisseurs
        (Nom_Fournisseur, Article, Quantite, Date_de_Reception, Priorite)
        VALUES (?, ?, ?, ?, ?)

        Les données sont récupérées dynamiquement depuis la liste Data

6. Fermeture de la connexion SQL

    Une fois toutes les insertions terminées, la connexion SQL est fermée proprement


<img width="1340" height="703" alt="Image" src="https://github.com/user-attachments/assets/fadb3325-8ae6-48f9-a20e-e74ad0c8b3f0" />

<img width="1368" height="752" alt="Image" src="https://github.com/user-attachments/assets/9f49da6c-c4f4-4d58-839d-58572f1d5c0c" />

