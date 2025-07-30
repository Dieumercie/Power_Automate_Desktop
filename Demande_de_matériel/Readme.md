# Demandes de matériel par e-mail avec pièce jointe PDF

## 🎯 Objectif

Lire les e-mails reçus dans Outlook, télécharger les pièces jointes PDF contenant des demandes de matériel, en extrait les informations, et les enregistrer dans un fichier Excel.

## 📌 Contexte professionnel fictif

Chaque jour, des demandes de matériel sont envoyées par e-mail via Outlook. Ces demandes sont formalisées dans un fichier PDF joint. Le service des achats centralise toutes les demandes dans un fichier Excel.

## 🧪 Exemple de données
E-mail

    Objet :
    Demande de matériel - Dupont Alice

    Pièce jointe PDF :
    Contenu du PDF :

    Matériel : Souris sans fil  
    Quantité : 2  
    Priorité : Haute

✅ Étapes réalisées par le robot

    Lire les e-mails Outlook

        Récupérer les e-mails non lus dans la boîte de réception

    Filtrer les e-mails valides

        Objet doit commencer par Demande de matériel -

        Pièce jointe de type .pdf présente

    Télécharger la pièce jointe

        Enregistrer la pièce jointe dans un dossier temporaire (ex : C:\Demandes\PDF_Temp)

    Lire le contenu du fichier PDF

        Utiliser une extraction directe du texte selon le format

    Extraire les données suivantes

        Nom, Matériel, Quantité, Priorité, Date : extraits depuis le contenu PDF

    Ajouter les données dans un fichier Excel

        Le fichier doit contenir un tableau structuré avec les colonnes suivantes :
        Nom | Matériel | Quantité | Priorité | Date 

    Nettoyer les fichiers et marquer l’e-mail

        Supprimer le PDF temporaire





