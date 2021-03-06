---
title: Déboguer une application console .NET Core avec Visual Studio
description: Découvrez comment déboguer une application console .NET Core avec Visual Studio.
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4bd2a8a0e4b3cea55e209306dd3788552e4b61f3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005412"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>Didacticiel : déboguer une application console .NET Core à l’aide de Visual Studio

Ce didacticiel présente les outils de débogage disponibles dans Visual Studio.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio 2019](with-visual-studio.md).

## <a name="debug-build-configuration"></a>Configuration de build Debug

*Débogage* et *Mise en production* sont deux des configurations de build par défaut de Visual Studio. La configuration de build actuelle s’affiche sur la barre d’outils. L’image de barre d’outils suivante montre que Visual Studio est configuré pour compiler la version de débogage de l’application :

![Barre d’outils Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Commencez par exécuter la version de débogage de l’application. La configuration de la build Debug désactive la plupart des optimisations du compilateur et fournit des informations plus détaillées pendant le processus de génération.

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

<!-- markdownlint-disable MD025 -->

1. Définissez un *point d’arrêt* sur la ligne qui affiche le nom, la date et l’heure en cliquant dans la marge de gauche de la fenêtre de code sur cette ligne. Vous pouvez également définir un point d’arrêt en plaçant le curseur dans la ligne de code, puis en appuyant sur **F9** ou en choisissant **Déboguer**  >  **basculer le point d’arrêt** dans la barre de menus.

   Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* l’exécution de la ligne avec le point d’arrêt.

   Comme le montre l’illustration suivante, Visual Studio indique la ligne sur laquelle le point d’arrêt est défini en le mettant en surbrillance et en affichant un point rouge dans la marge de gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Exécutez le programme en mode débogage en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils. D’autres façons de démarrer le débogage sont en appuyant sur **F5** ou en choisissant **Déboguer**  >  **Démarrer le débogage**.

1. Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur **entrée**.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.

   ![Capture d’écran d’un point d’arrêt dans Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez. Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.

   1. Si la fenêtre **exécution** n’est pas visible, affichez-la en sélectionnant **Déboguer**les  >  **fenêtres**  >  **immédiates**.

   1. Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .

   1. Entrez `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .

   La fenêtre **exécution** affiche la valeur de la variable de chaîne et les propriétés de la <xref:System.DateTime> valeur. En outre, les valeurs des variables sont mises à jour dans la fenêtre variables **locales** .

   ![Variables locales et fenêtres immédiates dans Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Poursuivez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils. Pour continuer, vous pouvez également choisir **Déboguer**  >  **Continuer**.

   Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .

   ![Fenêtre de console présentant les valeurs entrées](./media/debugging-with-visual-studio/console-window.png)

1. Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.

## <a name="set-a-conditional-breakpoint"></a>Définir un point d’arrêt conditionnel

Le programme affiche la chaîne que l’utilisateur entre. Que se passe-t-il si l’utilisateur n’entre rien ? Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*, qui interrompt l’exécution du programme quand une ou plusieurs conditions sont remplies.

Pour définir un point d’arrêt conditionnel et voir ce qu’il se passe lorsque l’utilisateur n’entre pas de chaîne, procédez comme suit :

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **conditions** pour ouvrir la boîte de dialogue **paramètres de point d’arrêt** . Activez la case à cocher des **conditions** si elle n’est pas déjà sélectionnée.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pour l' **expression conditionnelle**, entrez le code suivant dans le champ qui montre un exemple de code qui teste si a la touche `x` 5. Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .

   Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre spécifié de fois, ou une condition de *filtre*qui interrompt l’exécution du programme en fonction d’attributs tels que l’identificateur de thread, le nom de processus ou le nom de thread.

1. Sélectionnez **Fermer** pour fermer la boîte de dialogue.

1. Démarrez le programme avec le débogage en appuyant sur **F5**.

1. Dans la fenêtre de la console, appuyez sur la touche **entrée** lorsque vous êtes invité à entrer votre nom.

1. Étant donné que la condition que vous avez spécifiée ( `name` a la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la `Console.WriteLine` méthode s’exécute.

1. Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution. Dans ce cas, `Main` est la méthode en cours d’exécution. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante dans la fenêtre **exécution** et en appuyant sur **entrée**. Le résultat est `true`.

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   Le point d’interrogation dirige la fenêtre exécution pour [évaluer une expression](/visualstudio/ide/reference/immediate-window#enter-commands).

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

1. Effacez le point d’arrêt en cliquant sur le point dans la marge de gauche de la fenêtre de code. Une autre façon de supprimer un point d’arrêt consiste à choisir **Déboguer > basculer le point d’arrêt** pendant que la ligne de code est sélectionnée.

## <a name="step-through-a-program"></a>Parcourir un programme

Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution. En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme. Étant donné que votre programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.

1. Choisissez **Déboguer**  >  **pas à pas**détaillé. Vous pouvez également déboguer une instruction à la fois en appuyant sur **F11**.

   Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   C#

   ![Méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   À ce stade, la fenêtre **variables locales** indique que le `args` tableau est vide et `name` possède les `date` valeurs par défaut. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Appuyez sur **F11**. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. La fenêtre **variables locales** est inchangée et la fenêtre de console reste vide.

   C#

   ![Source de la méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Source de la méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **variables locales** affiche la `name` `null` valeur et la fenêtre de console affiche la chaîne « quel est votre nom ? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur **entrée**. La console ne répond pas et la chaîne que vous avez entrée n’est pas affichée dans la fenêtre de console, mais la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode capture néanmoins votre entrée.

1. Appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui comprend l' `date` affectation de la variable ( `currentDate` dans Visual Basic). La fenêtre **variables locales** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode. La fenêtre de console affiche également la chaîne que vous avez entrée à l’invite.

1. Appuyez sur **F11**. La fenêtre **variables locales** affiche la valeur de la `date` variable après l’affectation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété. La fenêtre de console est inchangée.

1. Appuyez sur **F11**. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. La fenêtre de console affiche la chaîne mise en forme.

1. Choisissez **Déboguer**  >  **pas à pas sortant**. Pour arrêter l’exécution pas à pas, vous pouvez également appuyer sur **MAJ** + **F11**.

   La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

## <a name="build-a-release-version"></a>Créer une version Release

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release. La version Release intègre des optimisations du compilateur qui peuvent parfois affecter négativement le comportement d’une application. Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.

Pour générer et tester la version Release de votre application console, changez la configuration de build dans la barre d’outils de **Debug** en **Release**.

![Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Quand vous appuyez sur **F5** ou que vous choisissez **générer la solution** dans le menu **générer** , Visual Studio compile la version Release de l’application. Vous pouvez le tester comme vous l’avez fait pour la version de débogage.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez utilisé les outils de débogage de Visual Studio. Dans le didacticiel suivant, vous allez publier une version déployable de l’application.

> [!div class="nextstepaction"]
> [Publier une application console .NET Core avec Visual Studio](publishing-with-visual-studio.md)
