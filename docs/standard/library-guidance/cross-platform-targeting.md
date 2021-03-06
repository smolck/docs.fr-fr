---
title: Ciblage multiplateforme pour les bibliothèques .NET
description: Meilleures pratiques recommandées pour la création de bibliothèques .NET multiplateformes.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731451"
---
# <a name="cross-platform-targeting"></a>Ciblage multiplateforme

L’infrastructure .NET moderne prend en charge plusieurs systèmes d’exploitation et appareils. Il est important que les bibliothèques .NET open source prennent en charge autant de développeurs que possible, que ce soit pour développer un site Web ASP.NET hébergé dans Azure ou un jeu .NET dans Unity.

## <a name="net-standard"></a>.NET Standard

.NET Standard est la meilleure façon d’ajouter une prise en charge multiplateforme à une bibliothèque .NET. [.NET Standard](../net-standard.md) est une spécification des API .NET disponibles sur toutes les implémentations de .NET. Le ciblage .NET Standard vous permet de générer des bibliothèques contraintes d’utiliser des API qui se trouvent dans une version donnée de .NET Standard, ce qui signifie qu’il est utilisable par toutes les plateformes qui implémentent cette version de .NET Standard.

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Le ciblage .NET Standard et la compilation avec succès de votre projet ne garantissent pas que la bibliothèque fonctionne correctement sur toutes les plateformes :

1. des API propres à une plateforme échoueront sur d’autres plateformes. Par exemple, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> réussiront sur Windows mais lèveront une exception <xref:System.PlatformNotSupportedException> s’ils sont utilisés sur n’importe quel autre système d’exploitation.
2. Les API peuvent se comporter différemment. Par exemple, les API de réflexion ont des caractéristiques de performances différentes lorsqu’une application utilise la compilation AOT (Ahead Of Time) sur iOS ou UWP.

> [!TIP]
> L’équipe .NET [propose un analyseur Roslyn](../analyzers/api-analyzer.md) pour vous aider à détecter les éventuels problèmes.

✔️ À FAIRE : Commencer par inclure une cible `netstandard2.0`.

> La plupart des bibliothèques à usage général ne devraient pas avoir besoin d’API en dehors de .NET Standard 2.0. .NET Standard 2.0 est pris en charge par toutes les plateformes modernes et constitue la méthode recommandée pour prendre en charge plusieurs plateformes avec une cible.

❌AVOID y `netstandard1.x` compris une cible.

> .NET Standard 1.x est distribué sous la forme d’un ensemble précis de packages NuGet, qui crée un grand graphique des dépendances de package et amène les développeurs à télécharger un grand nombre de packages lors de la génération. Les plateformes .NET modernes, y compris .NET Framework 4.6.1, UWP et Xamarin, prennent toutes en charge .NET Standard 2.0. Vous devez uniquement cibler .NET Standard 1.x si vous avez besoin de cibler une plateforme plus ancienne.

✔️ À FAIRE  : Inclure une cible `netstandard2.0` si vous avez besoin d’une cible `netstandard1.x`.

> Toutes les plateformes prenant en charge .NET Standard 2.0 utiliseront la cible `netstandard2.0` et bénéficieront d’un graphique de packages plus petit, tandis que les anciennes plateformes continueront de fonctionner et utiliseront la cible `netstandard1.x`.

❌NE PAS inclure une cible standard .NET si la bibliothèque s’appuie sur un modèle d’application spécifique à la plate-forme.

> Par exemple, une bibliothèque de boîte à outils de contrôle UWP dépend d’un modèle d’application uniquement disponible sur UWP. Les API spécifiques à un modèle d’application ne seront pas disponibles dans .NET Standard.

## <a name="multi-targeting"></a>Multi-ciblage

Parfois, vous avez besoin accéder à des API spécifiques à une infrastructure à partir de vos bibliothèques. La meilleure façon d’appeler des API spécifiques à une infrastructure consiste à utiliser le multi-ciblage, qui génère votre projet pour un grand nombre [d’infrastructures .NET cible](../frameworks.md) plutôt que pour une seule.

Pour éviter à vos consommateurs d’avoir à créer pour chaque infrastructure, vous devez vous efforcer d’avoir une sortie Standard .NET ainsi qu’une ou plusieurs sorties spécifiques à l’infrastructure. Avec le multi-ciblage, tous les assemblys sont empaquetés dans un même package NuGet. Les consommateurs peuvent ensuite référencer le même package, et NuGet choisit l’implémentation appropriée. Votre bibliothèque .NET Standard sert de bibliothèque de secours utilisée partout, sauf si votre package NuGet offre une implémentation spécifique à une infrastructure. Le multi-ciblage permet d’utiliser la compilation conditionnelle dans votre code et d’appeler des API spécifiques à une infrastructure.

![Forfait NuGet avec plusieurs assemblages](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Forfait NuGet avec plusieurs assemblages")

✔️ À ENVISAGER : cibler des implémentations .NET en plus de .NET Standard.

> Le ciblage d’implémentations .NET vous permet d’appeler des API spécifiques à la plateforme qui sont trouvent en dehors de .NET Standard.
>
> Ne supprimez pas la prise en charge de .NET Standard lorsque vous effectuez cette opération. Au lieu de cela, levez une exception à partir de l’implémentation et offrez la fonctionnalité API. De cette façon, votre bibliothèque peut être utilisée partout et prend en charge le runtime des fonctionnalités.

```csharp
public static class GpsLocation
{
    // This project uses multi-targeting to expose device-specific APIs to .NET Standard.
    public static async Task<(double latitude, double longitude)> GetCoordinatesAsync()
    {
#if NET461
        return CallDotNetFramworkApi();
#elif WINDOWS_UWP
        return CallUwpApi();
#else
        throw new PlatformNotSupportedException();
#endif
    }

    // Allows callers to check without having to catch PlatformNotSupportedException
    // or replicating the OS check.
    public static bool IsSupported
    {
        get
        {
#if NET461 || WINDOWS_UWP
            return true;
#else
            return false;
#endif
        }
    }
}
```

❌AVOID multi-ciblage ainsi que le ciblage .NET Standard, si votre code source est le même pour toutes les cibles.

> L’assembly .NET Standard sera automatiquement utilisé par NuGet. Le ciblage d’implémentations .NET individuelles augmente la taille `*.nupkg` sans apporter d’avantage.

✔️ À ENVISAGER : Ajouter une cible pour `net461` lorsque que vous proposez une cible `netstandard2.0`.

> L’utilisation de .NET Standard 2.0 dans .NET Framework entraîne certains problèmes qui ont été résolus dans .NET Framework 4.7.2. Vous pouvez améliorer l’expérience des développeurs qui utilisent toujours .NET Framework 4.6.1 - 4.7.1 en leur offrant un fichier binaire conçu pour .NET Framework 4.6.1.

✔️ À FAIRE : Distribuer votre bibliothèque à l’aide d’un package NuGet.

> NuGet sélectionnera la meilleure cible pour les développeurs et leur évitera d’avoir à choisir l’implémentation appropriée.

✔️ À FAIRE : Utiliser la propriété `TargetFrameworks` d’un fichier projet lors du multi-ciblage.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️ À ENVISAGER : Utiliser [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) lors du multi-ciblage pour UWP et Xamarin car cela simplifie considérablement votre fichier projet.

## <a name="older-targets"></a>Anciennes cibles

.NET prend en charge le ciblage de versions .NET Framework qui ne sont plus prises en charge depuis longtemps, ainsi que les plateformes qui ne sont plus couramment utilisées. Bien qu'il soit utile de faire fonctionner votre bibliothèque sur autant de cibles que possible, le fait de devoir contourner des API manquantes peut entraîner d’importants frais généraux. Nous estimons que certaines infrastructures ne valent plus la peine d'être ciblées, compte tenu de leur portée et de leurs limites.

❌NE PAS inclure une cible de bibliothèque de classe portable (PCL). Par exemple : `portable-net45+win8+wpa81+wp8`.

> .NET standard est la méthode moderne de prendre en charge les bibliothèques .NET multiplateformes et remplace les PCL.

❌NE PAS inclure les cibles pour les plates-formes .NET qui ne sont plus prises en charge. Par exemple, `SL4`, `WP`.

>[!div class="step-by-step"]
>[Suivant précédent](get-started.md)
>[Next](strong-naming.md)
