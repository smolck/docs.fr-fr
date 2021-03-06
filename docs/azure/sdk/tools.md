---
title: Outils pour les développeurs Azure .NET et .NET Core
description: Obtenez les outils pour commencer à utiliser les bibliothèques .NET Azure à partir d’un environnement Windows, Linux et Mac.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071940"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a>Outils pour les développeurs Azure .NET et .NET Core

## <a name="sdk-downloads"></a>Téléchargements du SDK

Les bibliothèques Azure pour .NET sont implémentées en tant que [packages NuGet](https://www.nuget.org/packages?q=windowsazureofficial). Consultez les informations de référence sur l' [API](/dotnet/api/overview/azure/?view=azure-dotnet) pour obtenir des instructions d’installation organisées par service Azure.

## <a name="development-tools"></a>Outils de développement

Visual Studio propose des outils pour de nombreux services Azure intégrés. Certains services Azure disposent d’outils ou d’émulateurs supplémentaires, comme [Explorateur stockage Azure](https://azure.microsoft.com/features/storage-explorer/). Consultez la documentation de votre service Azure pour obtenir des outils supplémentaires, si nécessaire.

Ces instructions installent l’environnement de développement recommandé pour votre système d’exploitation.

## <a name="windows"></a>[Windows](#tab/windows)

Les versions 2017 et ultérieures de Visual Studio offrent une prise en charge intégrée pour le développement Azure. Les étapes ci-dessous décrivent l’activation de la prise en charge du développement Azure dans Visual Studio.

Pour Visual Studio 2015 et versions antérieures, <a href="vs2015-install.md">suivez ces instructions</a>.

### <a name="step-1-download-visual-studio-2019"></a>Étape 1 : Télécharger Visual Studio 2019

Vous pouvez ignorer cette étape si vous avez déjà installé Visual Studio 2019.

> [!div class="nextstepaction"]
> [Télécharger Visual Studio 2019](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>Étape 2 : Installer les deux charges de travail Azure

Dans le programme d’installation de Visual Studio, installez Visual Studio (ou modifiez une installation existante). Assurez-vous que les charges de travail *développement Azure* et développement *Web et ASP.net* sont sélectionnées.

### <a name="step-3-develop-with-net-on-azure"></a>Étape 3 : Développer avec .NET sur Azure

Commencez par [déployer votre première application web ASP.NET Core sur Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).

## <a name="macos"></a>[macOS](#tab/macos)

Visual Studio pour Mac contient tout ce dont vous avez besoin pour le développement Azure.

### <a name="step-1-download-visual-studio-for-mac"></a>Étape 1 : Télécharger Visual Studio pour Mac

> [!div class="nextstepaction"]
> [Télécharger Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

Au cours de l’installation, les outils Azure sont sélectionnés par défaut.

## <a name="linux"></a>[Linux](#tab/linux)

Visual Studio Code contient tout ce dont vous avez besoin pour le développement Azure sur Linux.

### <a name="step-1-download-the-net-core-sdk"></a>Étape 1 : Télécharger le kit SDK .NET Core

Le Kit de développement logiciel (SDK) et les outils de ligne de commande pour les applications .NET Core.

> [!div class="nextstepaction"]
> [Télécharger le kit de développement logiciel (SDK) .NET Core](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>Étape 2 : Visual Studio Code

Modifiez et déboguez des applications .NET Core sur n’importe quel système d’exploitation : Windows, Mac et Linux.

> [!div class="nextstepaction"]
> [Télécharger Visual Studio Code](https://code.visualstudio.com)

---
