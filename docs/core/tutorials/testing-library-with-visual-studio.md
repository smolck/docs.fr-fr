---
title: Tester une bibliothèque de classes .NET Standard avec .NET Core dans Visual Studio
description: Créez un projet de test unitaire pour votre bibliothèque de classes .NET Core. Vérifiez que votre bibliothèque de classes .NET Core fonctionne correctement avec des tests unitaires.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 79b680022484bb9222b66c3df76bdd5a06de8117
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005009"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio"></a>Didacticiel : tester une bibliothèque .NET Standard avec .NET Core dans Visual Studio

Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md).

## <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

1. Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md).

1. Ajoutez un nouveau projet de test unitaire nommé « StringLibraryTest » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , entrez **MSTest** dans la zone de recherche. Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.

   1. Choisissez le modèle **projet de test MSTest (.net Core)** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **StringLibraryTest** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

   > [!NOTE]
   > MSTest est l’un des trois frameworks de test que vous pouvez choisir. Les autres sont xUnit et nUnit.

1. Visual Studio crée le projet et ouvre le fichier de classe dans la fenêtre de code avec le code suivant. Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   Le code source créé par le modèle de test unitaire effectue les opérations suivantes :

   - Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.
   - Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`.
   - Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à définir `TestMethod1` en C# ou `TestSub` dans Visual Basic.

   Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **dépendances** du projet **StringLibraryTest** et sélectionnez **Ajouter une référence de projet** dans le menu contextuel.

1. Dans la boîte de dialogue **Gestionnaire de références** , développez le nœud **projets** , puis activez la case à cocher en regard de **StringLibrary**. L’ajout d’une référence à l' `StringLibrary` assembly permet au compilateur de rechercher des méthodes **StringLibrary** lors de la compilation du projet **StringLibraryTest** .

1. Sélectionnez **OK**.

## <a name="add-and-run-unit-test-methods"></a>Ajouter et exécuter des méthodes de test unitaire

Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut. Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :

| Méthodes d’assertion     | Fonction |
| ------------------ | -------- |
| `Assert.AreEqual`  | Vérifie que deux valeurs ou objets sont égaux. L’assertion échoue si les valeurs ou les objets ne sont pas égaux. |
| `Assert.AreSame`   | Vérifie que deux variables d’objet référencent le même objet. L’assertion échoue si les variables font référence à des objets différents. |
| `Assert.IsFalse`   | Vérifie qu’une condition est `false`. L’assertion échoue si la condition est `true`. |
| `Assert.IsNotNull` | Vérifie qu’un objet n’est pas `null` . L’assertion échouera si l’objet est `null`. |

Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever. Le test échoue si l’exception spécifiée n’est pas levée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule. Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>. De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule. Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.

Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> a la valeur 0, et une `null` chaîne qui n’a pas été initialisée. Si `StartsWithUpper` est appelé en tant que méthode d’extension sur une <xref:System.String> instance, une chaîne ne peut pas être passée `null` . Toutefois, vous pouvez également l’appeler directement comme méthode statique et passer un seul argument <xref:System.String>.

Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode à plusieurs reprises pour chaque élément d’un tableau de chaînes. Étant donné que la méthode de test échoue dès qu’elle trouve le premier échec, vous appelez une surcharge de méthode qui vous permet de passer une chaîne qui indique la valeur de chaîne utilisée dans l’appel de méthode.

Pour créer les méthodes de test:

1. Dans la fenêtre de code *UnitTest1.cs* ou *UnitTest1. vb* , remplacez le code par le code suivant :

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C). Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).

1. Dans la barre de menus, sélectionnez **fichier**  >  **Enregistrer UnitTest1.cs sous** ou enregistrer le **fichier**  >  **UnitTest1. VB sous**. Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue Enregistrer le fichier sous Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.

1. Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue Options d’enregistrement avancées dans Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII. Lorsque cela se produit, le runtime ne décode pas correctement les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne sont pas corrects.

1. Dans la barre de menus, sélectionnez **tester**  >  **exécuter tous les tests**. Si la fenêtre **Explorateur de tests** ne s’ouvre pas, ouvrez-la en sélectionnant **tester**l'  >  **Explorateur de tests**. Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.

   > [!div class="mx-imgBorder"]
   > ![Fenêtre Explorateur de tests avec tests réussis](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Gérer les échecs de test

Votre série de tests n’a rencontré aucun échec : changez-la légèrement de façon à faire échouer une des méthodes de test :

1. Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ». Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Exécutez le test en sélectionnant **test**  >  **exécuter tous les tests** dans la barre de menus. La fenêtre **Explorateur de tests** indique que deux tests ont réussi et qu’un test a échoué.

   > [!div class="mx-imgBorder"]
   > ![Fenêtre Explorateur de tests avec tests ayant échoué](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Sélectionnez le test qui a échoué, `TestDoesNotStartWith` . La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse. « Erreur » : false ; réel : True » était attendu ». En raison de l’échec, toutes les chaînes du tableau après « erreur » n’ont pas été testées.

   > [!div class="mx-imgBorder"]
   > ![Fenêtre Explorateur de tests présentant l’échec de l’assertion IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Annulez la modification que vous avez effectuée à l’étape 1 en supprimant la chaîne « Error ». Réexécutez le test et les tests réussissent.

## <a name="test-the-release-version-of-the-library"></a>Tester la version Release de la bibliothèque

Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

Pour tester la version Release :

1. Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.

   > [!div class="mx-imgBorder"]
   > ![Barre d’outils Visual Studio avec version Release mise en surbrillance](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.

   > [!div class="mx-imgBorder"]
   > ![Menu contextuel de StringLibrary avec commande build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Exécutez les tests unitaires en choisissant **test exécuter**  >  **tous les tests** dans la barre de menus. Les tests réussissent.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Concepts de base des tests unitaires-Visual Studio](/visualstudio/test/unit-test-basics)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez testé une bibliothèque de classes. Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package. Pour en savoir plus, suivez un didacticiel NuGet :

> [!div class="nextstepaction"]
> [Créer et publier un package NuGet à l’aide de Visual Studio](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser. Pour en savoir plus, suivez un didacticiel NuGet :

> [!div class="nextstepaction"]
> [Installer et utiliser un package dans Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

Une bibliothèque n’a pas besoin d’être distribuée en tant que package. Il peut être fourni avec une application console qui l’utilise. Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :

> [!div class="nextstepaction"]
> [Publier une application console .NET Core avec Visual Studio](publishing-with-visual-studio.md)
