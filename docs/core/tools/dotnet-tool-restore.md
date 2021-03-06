---
title: dotnet outil restaurer la commande
description: L’outil dotnet restaurer la commande installe sur votre machine les outils locaux .NET Core qui sont en portée pour l’annuaire actuel.
ms.date: 02/14/2020
ms.openlocfilehash: a518c2d45bbe9522bddfed4bbef61b30f1ad634b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463342"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet tool restore`- Installe sur votre machine les outils locaux .NET Core qui sont en portée pour l’annuaire actuel.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a>Description

La `dotnet tool restore` commande trouve le fichier manifeste de l’outil qui est en portée pour l’annuaire actuel et installe les outils qui y sont répertoriés. Pour plus d’informations sur les fichiers manifestes, voir [Installer un outil local](global-tools.md#install-a-local-tool) et [invoquer un outil local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

Nom/ID du paquet NuGet qui contient l’outil .NET Core à installer.

## <a name="options"></a>Options

- **`--configfile <FILE>`**

  Fichier de configuration NuGet (*nuget.config*) à utiliser.

- **`--add-source <SOURCE>`**

  Ajoute une source de package NuGet supplémentaire à utiliser pendant l’installation.

- **`--tool-manifest <PATH>`**

  Chemin vers le fichier manifeste.

- **`--disable-parallel`**

  Empêcher la restauration de plusieurs projets en parallèle.

- **`--ignore-failed-sources`**

  Traiter les défaillances des sources de colis comme des avertissements.

- **`--no-cache`**

  Ne cachez pas les paquets et les demandes http.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

## <a name="example"></a>Exemple

- **`dotnet tool restore`**

  Restaure les outils locaux pour l’annuaire actuel.

## <a name="see-also"></a>Voir aussi

- [.NET Outils de base](global-tools.md)
- [Tutorial: Installer et utiliser un outil local .NET Core en utilisant le CLI .NET Core](local-tools-how-to-use.md)
