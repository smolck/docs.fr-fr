---
title: Effectuer des tests unitaires du code C# dans .NET Core à l’aide de dotnet test et de xUnit
description: Apprenez les concepts des tests unitaires dans C# et .NET Core de manière interactive en créant un exemple de solution pas à pas à l’aide de dotnet test et de xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d8cf0e29c8a482b39bd7e99bcde1fd60301f046f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702952"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Effectuer des tests unitaires de C# dans .NET Core à l’aide de dotnet test et de xUnit

Ce didacticiel montre comment générer une solution contenant un projet de test unitaire et un projet de code source. Pour suivre le didacticiel à l’aide d’une solution prédéfinie, [Affichez ou téléchargez l’exemple de code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Créez la solution

Dans cette section, une solution qui contient les projets source et de test est créée. La solution terminée présente la structure de répertoire suivante :

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

Les instructions suivantes fournissent les étapes permettant de créer la solution de test. Consultez [commandes pour créer une solution de test](#create-test-cmd) pour obtenir des instructions sur la création d’une solution de test en une seule étape.

* Ouvrez une fenêtre d’interpréteur de commandes.
* Exécutez la commande suivante :

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  La [`dotnet new sln`](../tools/dotnet-new.md) commande crée une nouvelle solution dans le répertoire *Unit-testing-using-dotnet-test* .
* Remplacez le répertoire par le dossier *Unit-testing-using-dotnet-test* .
* Exécutez la commande suivante :

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   La [`dotnet new classlib`](../tools/dotnet-new.md) commande crée un projet de bibliothèque de classes dans le dossier *PrimeService* . La nouvelle bibliothèque de classes contiendra le code à tester.
* Renommez *Class1.cs* en *PrimeService.cs*.
* Remplacez le code dans *PrimeService.cs* par le code suivant :
  
  ```csharp
  using System;

  namespace Prime.Services
  {
      public class PrimeService
      {
          public bool IsPrime(int candidate)
          {
              throw new NotImplementedException("Not implemented.");
          }
      }
  }
  ```

* Le code précédent :
  * Lève une exception <xref:System.NotImplementedException> avec un message indiquant qu’elle n’est pas implémentée.
  * Est mis à jour ultérieurement dans le didacticiel.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* Dans le répertoire *Unit-testing-using-dotnet-test* , exécutez la commande suivante pour ajouter le projet de bibliothèque de classes à la solution :

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Créez le projet *PrimeService. tests* en exécutant la commande suivante :

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* La commande précédente :
  * Crée le projet *PrimeService. tests* dans le répertoire *PrimeService. tests* . Le projet de test utilise [xUnit](https://xunit.net/) comme bibliothèque de test.
  * Configure Test Runner en ajoutant les `<PackageReference />` éléments suivants au fichier projet :
    * « Microsoft. NET. test. Sdk »
    * xUnit
    * « xUnit. Runner. VisualStudio »

* Ajoutez le projet de test au fichier solution en exécutant la commande suivante :

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Ajoutez la `PrimeService` bibliothèque de classes en tant que dépendance au projet *PrimeService. tests* :

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Commandes pour créer la solution

Cette section résume toutes les commandes de la section précédente. Ignorez cette section si vous avez effectué les étapes décrites dans la section précédente.

Les commandes suivantes créent la solution de test sur un ordinateur Windows. Pour macOS et UNIX, mettez à jour la `ren` commande vers la version du système d’exploitation de `ren` pour renommer un fichier :

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

Suivez les instructions pour « remplacer le code dans *PrimeService.cs* par le code suivant » dans la section précédente.

## <a name="create-a-test"></a>Créer un test

Une approche courante du développement piloté par les tests (TDD) consiste à écrire un test avant d’implémenter le code cible. Ce didacticiel utilise l’approche TDD. La `IsPrime` méthode peut être appelée, mais elle n’est pas implémentée. Un appel de test à `IsPrime` échoue. Avec TDD, un test est écrit et connu comme ayant échoué. Le code cible est mis à jour pour que le test réussisse. Vous continuez à répéter cette approche, en écrivant un test qui a échoué, puis en mettant à jour le code cible pour qu’il réussisse.

Mettez à jour le projet *PrimeService. tests* :

* Supprimez *PrimeService. tests/UnitTest1. cs*.
* Créez un fichier *PrimeService. tests/PrimeService_IsPrimeShould. cs* .
* Remplacez le code dans *PrimeService_IsPrimeShould. cs* par le code suivant :

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

L' `[Fact]` attribut déclare une méthode de test qui est exécutée par Test Runner. À partir du dossier *PrimeService. tests* , exécutez `dotnet test` . La commande [dotnet test](../tools/dotnet-test.md) génère les deux projets et exécute les tests. Le test Runner xUnit contient le point d’entrée de programme pour exécuter les tests. `dotnet test`démarre le testeur de test à l’aide du projet de test unitaire.

Le test échoue car `IsPrime` n’a pas été implémenté. À l’aide de l’approche TDD, écrivez uniquement le code suffisant pour que ce test soit réussi. Mettez à jour `IsPrime` avec le code suivant :

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Exécutez `dotnet test`. Le test réussit.

### <a name="add-more-tests"></a>Ajouter d’autres tests

Ajoutez des tests de nombre premier pour 0 et-1. Vous pouvez copier le test précédent et modifier le code suivant pour utiliser 0 et-1 :

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

La copie du code de test lorsque seul un paramètre change entraîne la duplication du code et l’augmentation des tests. Les attributs xUnit suivants permettent d’écrire une suite de tests similaires :

- `[Theory]` représente une suite de tests qui exécutent le même code, mais qui ont des arguments d’entrée différents.
- L’attribut `[InlineData]` spécifie des valeurs pour ces entrées.

Au lieu de créer de nouveaux tests, appliquez les attributs xUnit précédents pour créer une théorie unique. Remplacez le code suivant :

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

par le code suivant :

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Dans le code précédent, `[Theory]` et `[InlineData]` permettent de tester plusieurs valeurs inférieures à deux. Deux est le plus petit nombre premier.

Exécuter `dotnet test` , deux des tests échouent. Pour que tous les tests réussissent, mettez à jour la `IsPrime` méthode avec le code suivant :

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Après l’approche TDD, ajoutez d’autres tests ayant échoué, puis mettez à jour le code cible. Consultez la [version finale des tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) et l' [implémentation complète de la bibliothèque](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

La `IsPrime` méthode terminée n’est pas un algorithme efficace pour tester primality.

### <a name="additional-resources"></a>Ressources supplémentaires

- [Site officiel xUnit.net](https://xunit.net)
- [Test de la logique de contrôleur dans ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
