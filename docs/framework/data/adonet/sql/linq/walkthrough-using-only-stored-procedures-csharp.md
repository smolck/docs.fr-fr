---
title: 'Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f980402c976db9ee327a7b726e36a0a4d9d6d73f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792111"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)

Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de base de bout en bout pour accéder aux données en exécutant des procédures stockées uniquement. Cette approche est souvent utilisée par les administrateurs de base de données pour limiter les moyens d'accès au magasin de données.

> [!NOTE]
> Vous pouvez également utiliser des procédures stockées dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour substituer le comportement par défaut, plus particulièrement pour les processus `Create`, `Update` et `Delete`. Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).

Dans le cadre de cette procédure pas à pas, vous allez utiliser deux méthodes qui ont été mappées à des procédures stockées dans l’exemple de base de données Northwind : CustOrdersDetail et CustOrderHist. Le mappage se produit lorsque vous exécutez l'outil en ligne de commande SQLMetal pour générer un fichier C#. Pour plus d'informations, consultez la section Composants requis par la suite dans cette procédure pas à pas.

Cette procédure pas à pas ne repose pas sur le Concepteur Objet Relationnel. Les développeurs qui utilisent Visual Studio peuvent également utiliser le Concepteur O/R pour implémenter les fonctionnalités de procédure stockée. Consultez [LINQ to SQL Tools dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.

## <a name="prerequisites"></a>Prérequis

Elle requiert les éléments suivants :

- Les fichiers sont stockés dans un dossier dédié, c:\linqtest7. Vous devez créer ce dossier avant de commencer la procédure pas à pas.

- Exemple de base de données Northwind.

     Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md). Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest7.

- Fichier de code C# généré à partir de la base de données Northwind.

     Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :

     **sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**

     Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).

## <a name="overview"></a>Présentation

Cette procédure pas à pas se compose de six tâches principales :

- Configuration de la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution dans Visual Studio.

- Ajout de l'assembly System.Data.Linq au projet.

- Ajout du fichier de code de base de données au projet.

- Création d'une connexion à la base de données.

- Configuration de l'interface utilisateur.

- Exécution et test de l'application.

## <a name="creating-a-linq-to-sql-solution"></a>Création d'une solution LINQ to SQL

Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] un projet.

### <a name="to-create-a-linq-to-sql-solution"></a>Pour créer une solution LINQ to SQL

1. Dans le menu **fichier** de Visual Studio, pointez sur **nouveau**, puis cliquez sur **projet**.

2. Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **visuel C#** .

3. Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.

4. Dans la zone **nom** , tapez **SprocOnlyApp**.

5. Dans la zone **emplacement** , vérifiez l’emplacement où vous souhaitez stocker vos fichiers projet.

6. Cliquez sur **OK**.

     Le Concepteur Windows Forms s'ouvre.

## <a name="adding-the-linq-to-sql-assembly-reference"></a>Ajout de la référence à l'assembly LINQ to SQL

L'assembly [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] n'est pas inclus dans le modèle Application Windows Forms standard. Vous devrez ajouter l'assembly vous-même, comme expliqué dans les étapes suivantes :

### <a name="to-add-systemdatalinqdll"></a>Pour ajouter System.Data.Linq.dll

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.

     L'assembly est ajouté au projet.

## <a name="adding-the-northwind-code-file-to-the-project"></a>Ajout du fichier de code Northwind au projet

Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind. Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.

### <a name="to-add-the-northwind-code-file-to-the-project"></a>Pour ajouter le fichier de code Northwind au projet

1. Dans le menu **projet** , cliquez sur **Ajouter un élément existant**.

2. Dans la boîte de dialogue **Ajouter un élément existant** , accédez à c:\linqtest7\northwind.cs, puis cliquez sur **Ajouter**.

     Le fichier northwind.cs est ajouté au projet.

## <a name="creating-a-database-connection"></a>Création d'une connexion à une base de données

Au cours de cette étape, vous allez définir la connexion à l'exemple de base de données Northwind. Cette procédure pas à pas utilise "c:\linqtest7\northwnd.mdf" comme chemin d’accès.

### <a name="to-create-the-database-connection"></a>Pour créer la connexion de base de données

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.cs**, puis cliquez sur **afficher le code**.

2. Tapez le code suivant dans la classe `Form1` :

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a>Configuration de l'interface utilisateur.

Au cours de cette tâche, vous configurez une interface afin que les utilisateurs puissent exécuter des procédures stockées pour accéder aux données dans la base de données. Dans les applications que vous développez avec cette procédure pas à pas, les utilisateurs peuvent accéder aux données dans la base de données uniquement en utilisant les procédures stockées incorporées dans l'application.

### <a name="to-set-up-the-user-interface"></a>Pour configurer l'interface utilisateur

1. Revenez au Concepteur Windows Forms (**Form1. cs [Design]** ).

2. Dans le menu **Affichage** , cliquez sur **Boîte à outils**.

     La boîte à outils s'ouvre.

    > [!NOTE]
    > Cliquez sur le punaise **Masquer automatiquement** pour maintenir la boîte à outils ouverte pendant que vous effectuez les étapes restantes de cette section.

3. Faites glisser deux boutons, deux zones de texte et deux étiquettes de la boîte à outils vers **Form1**.

     Disposez les contrôles comme dans l'illustration associée. Développez **Form1** afin que les contrôles s’ajustent facilement.

4. Cliquez avec le bouton droit sur **Label1**, puis cliquez sur **Propriétés**.

5. Modifiez la propriété **Text** de **Label1** en **Enter OrderID :** .

6. De la même façon pour **Label2**, modifiez la propriété **Text** de **Label2** en **Enter CustomerID :** .

7. De la même façon, modifiez la propriété **Text** de **Button1** en **Order Details**.

8. Modifiez la propriété **Text** de **button2** en **Order History**.

     Élargissez les contrôles boutons afin que tout le texte soit visible.

### <a name="to-handle-button-clicks"></a>Pour gérer des clics de bouton

1. Double-cliquez sur **Order Details** sur **Form1** pour ouvrir le gestionnaire d’événements Button1 dans l’éditeur de code.

2. Tapez le code suivant dans le gestionnaire d'événements `button1` :

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. Double-cliquez maintenant sur **button2** sur **Form1** pour ouvrir `button2` le gestionnaire

4. Tapez le code suivant dans le gestionnaire d'événements `button2` :

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a>Test de l'application

Vous allez maintenant tester votre application. Notez que votre contact avec le magasin de données est limité aux actions que les deux procédures stockées peuvent accepter. Ces actions consistent à retourner les produits inclus pour n'importe quel orderID que vous entrez ou à retourner un historique des produits commandés pour n'importe quel CustomerID que vous entrez.

### <a name="to-test-the-application"></a>Pour tester l'application

1. Appuyez sur F5 pour démarrer le débogage.

     Form1 s'affiche.

2. Dans la zone **Enter OrderID** , tapez `10249`, puis cliquez sur **Order Details**.

     Un message répertorie les produits inclus dans la commande 10249.

     Cliquez sur **OK** pour fermer la boîte de message.

3. Dans la zone **entrer CustomerID** , tapez `ALFKI`, puis cliquez sur **historique des commandes**.

     Le message qui apparaît répertorie l'historique des commandes pour le client ALFKI.

     Cliquez sur **OK** pour fermer la boîte de message.

4. Dans la zone **Enter OrderID** , tapez `123`, puis cliquez sur **Order Details**.

     Le message suivant s'affiche : « Aucun résultat ».

     Cliquez sur **OK** pour fermer la boîte de message.

5. Dans le menu **Déboguer** , cliquez sur **arrêter le débogage**.

     La session de débogage s'arrête.

6. Si vous avez terminé l’expérimentation, vous pouvez cliquer sur **Fermer le projet** dans le menu **fichier** et enregistrer votre projet lorsque vous y êtes invité.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez améliorer ce projet en apportant des modifications. Par exemple, vous pouvez répertorier les procédures stockées disponibles dans une zone de liste et demander à l'utilisateur de sélectionner les procédures à exécuter. Vous pouvez également transmettre en continu la sortie des rapports dans un fichier texte.

## <a name="see-also"></a>Voir aussi

- [Apprentissage par les procédures pas à pas](learning-by-walkthroughs.md)
- [Procédures stockées](stored-procedures.md)
