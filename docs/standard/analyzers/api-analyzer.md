---
title: Analyseur d’API .NET
description: Découvrez comment l’analyseur d’API .NET peut aider à détecter les problèmes de compatibilité de plateforme et les API déconseillées.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: e214c91f2beebc7f3b3324f4879deba9a5623f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156132"
---
# <a name="net-api-analyzer"></a>Analyseur d’API .NET

L’analyseur d’API .NET est un analyseur Roslyn qui détecte les risques potentiels liés à la compatibilité des API C# sur différentes plateformes, et détecte les appels à des API déconseillées. Il peut être utile à tous les développeurs C#, quel que soit le stade du développement.

L’analyseur d’API est fourni sous la forme d’un package NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Dès lors que vous y faites référence dans un projet, il effectue automatiquement le monitoring du code et indique l’utilisation d’API problématiques. Vous pouvez également obtenir des suggestions sur les corrections possibles en cliquant sur l’ampoule. Le menu déroulant comprend une option permettant de supprimer les avertissements.

> [!NOTE]
> L’analyseur d’API .NET est toujours en préversion.

## <a name="prerequisites"></a>Conditions préalables requises

- Visual Studio 2017 et versions ultérieures, ou Visual Studio pour Mac (toutes les versions).

## <a name="discover-deprecated-apis"></a>Découvrez les API dépréciées

### <a name="what-are-deprecated-apis"></a>Que sont les API déconseillées ?

La famille .NET est un ensemble de grands produits, qui sont constamment mis à niveau pour mieux répondre aux besoins des clients. Il est naturel de déconseiller certaines API et de les remplacer par d’autres. Une API est considérée comme déconseillées lorsqu’il existe une meilleure solution. Une API déconseillée, qu’il ne faut pas utiliser, peut être marquée avec l’attribut <xref:System.ObsoleteAttribute>. L’inconvénient de cette approche est qu’il n'existe qu’un seul ID de diagnostic pour toutes les API obsolètes (pour C#, [CS0612](../../csharp/misc/cs0612.md)). Cela signifie que :

- Il est impossible d’avoir un document dédié à chacun des cas.
- Il n’est pas possible de supprimer certaines catégories d’avertissements. On peut soit tous les supprimer, soit n’en supprimer aucun.
- Pour informer les utilisateurs qu’une API est à présent déconseillée, il faut mettre à jour un package de ciblage ou un assembly de référence.

L’analyseur d’API utilise des codes d’erreur propres aux API, qui commencent par DE (de l’anglais « Deprecation Error »), ce qui permet de contrôler l’affichage des différents avertissements. Les API déconseillées identifiées par l’analyseur sont définies dans le référentiel [dotnet/plateforme-compat](https://github.com/dotnet/platform-compat).

### <a name="add-the-api-analyzer-to-your-project"></a>Ajouter l’analyseur API à votre projet

1. Ouvrez Visual Studio.
2. Ouvrez le projet sur qui vous souhaitez exécuter l’analyseur.
3. Dans **Solution Explorer**, cliquez à droite sur votre projet et choisissez Manage **NuGet Packages**. (Cette option est également disponible dans le menu **Projet**.)
4. Sur l’onglet NuGet Package Manager :
   1. Sélectionnez «nuget.org» comme source de paquet.
   2. Allez à l’onglet **Parcourir.**
   3. Sélectionnez **Inclure la préversion**.
   4. Recherchez **Microsoft.DotNet.Analyzers.Compatibility**.
   5. Sélectionnez ce paquet dans la liste.
   6. Sélectionnez le bouton **Installer**.
   7. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

### <a name="use-the-api-analyzer"></a>Utilisez l’analyseur de l’API

Lorsqu’une API déconseillée, par exemple, <xref:System.Net.WebClient>, est utilisée dans un code, l’analyseur d’API la souligne d’un trait vert ondulé. Lorsque vous placez le curseur sur l’appel d’API, une ampoule donne des informations sur les API déconseillées, comme dans l’exemple suivant :

![« Capture d’écran de l’API WebClient avec une ligne verte ondulée et une ampoule à gauche »](media/api-analyzer/green-squiggle.jpg)

La fenêtre **Liste d’erreurs** contient des avertissements avec un ID unique par API déconseillée, comme dans l’exemple suivant (`DE004`) :

![« Capture d’écran de la fenêtre Liste d’erreurs affichant l’ID et la description de l’avertissement »](media/api-analyzer/warnings-id-and-descriptions.jpg "Fenêtre de liste d’erreurs qui comprend des avertissements.")

En cliquant sur l’ID, vous accédez à une page web présentant des informations détaillées sur la raison pour laquelle l’API a été déconseillée, ainsi que des suggestions d’autres API utilisables.

Pour supprimer des avertissements, cliquez sur le membre en surbrillance et sélectionnez **Supprimer \<ID de diagnostic >**. Il existe deux moyens de supprimer les avertissements :

- [localement (dans la source)](#suppress-warnings-locally) ;
- [globalement (dans un fichier de suppression)](#suppress-warnings-globally) – recommandé.

### <a name="suppress-warnings-locally"></a>Supprimer les avertissements localement

Pour supprimer les avertissements localement, cliquez à droite sur le membre que vous souhaitez supprimer les avertissements pour puis sélectionner **des actions rapides et des refactorings** > Supprimer diagnostic** *ID*\<ID ID>**  > dans **Source**. La directive du préprocesseur d’avertissement [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) est ajoutée à votre code source dans l’étendue définie : ![« Capture d’écran du code encadré par #pragma warning disable »](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppress-warnings-globally"></a>Supprimer les avertissements à l’échelle mondiale

Pour supprimer les avertissements à l’échelle mondiale, cliquez à droite sur le membre que vous souhaitez supprimer les avertissements pour puis sélectionner **des actions rapides et des refactorings** > Supprimer diagnostic** *ID*\<diagnostic ID>**  > dans le fichier de **suppression**.

![« Capture d’écran de l’API WebClient avec une ligne verte ondulée et une ampoule à gauche »](media/api-analyzer/suppress-in-sup-file.jpg)

Un fichier *GlobalSuppressions.cs* est ajouté à votre projet après la première suppression. Les nouvelles suppressions globales seront ajoutées à ce fichier.

![« Capture d’écran de l’API WebClient avec une ligne verte ondulée et une ampoule à gauche »](media/api-analyzer/suppression-file.jpg)

La suppression globale est la méthode recommandée pour garantir une utilisation cohérente de l’API d’un projet à l’autre.

## <a name="discover-cross-platform-issues"></a>Découvrez les enjeux interplateformes

Tout comme les API déconseillées, l’analyseur identifie toutes les API non multiplateformes. Par exemple, <xref:System.Console.WindowWidth?displayProperty=nameWithType> fonctionne sous Windows, mais pas sous Linux ou macOS. L’ID de diagnostic apparaît dans la fenêtre **Liste d’erreurs**. Vous pouvez supprimer cet avertissement en cliquant avec le bouton droit et en sélectionnant **Actions rapides et refactorisations**. Contrairement au cas des API déconseillées, dans lequel deux options sont proposées (continuer d’utiliser le membre déconseillé et supprimer les avertissements, ou ne pas l’utiliser du tout), ici, si vous développez votre code pour certaines plateformes seulement, vous pouvez supprimer les avertissements de toutes les autres plateformes sur lesquelles vous n’envisagez pas d’exécuter votre code. Il vous suffit pour cela de modifier votre fichier projet et d’ajouter la propriété `PlatformCompatIgnore`, qui liste toutes les plateformes à ignorer. Les valeurs acceptées sont les suivantes : `Linux`, `macOS` et `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Si votre code cible plusieurs plateformes et que vous souhaitez tirer parti d’une API non prise en charge sur certaines d'entre elles, vous pouvez protéger cette partie du code avec une instruction `if` :

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Vous pouvez également effectuer une compilation conditionnelle par système d’exploitation/version cible de .NET Framework ; il s’agit pour le moment d’une opération [manuelle](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Diagnostics pris en charge

Actuellement, l’analyseur gère les cas suivants :

- utilisation d’une API .NET Standard qui lève <xref:System.PlatformNotSupportedException> (PC001) ;
- utilisation d’une API .NET Standard non disponible sur .NET Framework 4.6.1 (PC002) ;
- utilisation d’une API native qui n’existe pas dans UWP (PC003) ;
- Utilisation des API Delegate.BeginInvoke et EndInvoke (PC004).
- utilisation d’une API marquée comme déconseillée (DEXXXX).

## <a name="ci-machine"></a>Machine de CI

Tous ces diagnostics sont disponibles non seulement dans l’IDE, mais également en ligne de commande dans le cadre de la création du projet, qui inclut le serveur de CI.

## <a name="configuration"></a>Configuration

L’utilisateur choisit le mode de traitement des diagnostics : en tant qu’avertissements, en tant qu’erreurs, en tant que suggestions ou désactivés. Par exemple, l’architecte peut décider que les problèmes de compatibilité doivent être traités comme des erreurs, que les appels à certaines API déconseillées génèrent des avertissements, tandis que les autres ne produiront que des suggestions. Vous pouvez configurer cela séparément, ID de diagnostic par ID de diagnostic et projet par projet. Pour cela, accédez au nœud **Dépendances** sous votre projet dans **l’Explorateur de solutions**. Élargir les **nœuds dépendances** > **Analyseurs** > **Microsoft.DotNet.Analyzers.Compatibility**. Cliquez avec le bouton droit sur l’ID de diagnostic, sélectionnez **Définir la gravité de l’ensemble de règles** et choisissez l’option souhaitée.

![« Capture d’écran de l’Explorateur de solutions affichant les diagnostics et la boîte de dialogue contextuelle avec la gravité de l’ensemble de règles »](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Voir aussi

- Billet de blog [Présentation de l’analyseur d’API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/).
- Vidéo de démonstration sur YouTube de [l’analyseur d’API](https://youtu.be/eeBEahYXGd0).
