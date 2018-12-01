---
title: Bien démarrer la création de bibliothèques .NET de haute qualité
description: Bien démarrer la création de bibliothèques .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6377e3fe606bf7603b418decdd0e3f9d2de6a510
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201241"
---
# <a name="get-started"></a><span data-ttu-id="79a55-103">Prise en main</span><span class="sxs-lookup"><span data-stu-id="79a55-103">Get started</span></span>

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[<span data-ttu-id="79a55-104">Ciblage multiplateforme</span><span class="sxs-lookup"><span data-stu-id="79a55-104">Cross-platform targeting</span></span>](./cross-platform-targeting.md)

<span data-ttu-id="79a55-105">Comment utiliser .NET Standard et le multi-ciblage pour créer des bibliothèques interplateformes.</span><span class="sxs-lookup"><span data-stu-id="79a55-105">How to use .NET Standard and multi-targeting to create cross-platform libraries.</span></span> <span data-ttu-id="79a55-106">.NET s’exécute dans de nombreux endroits, et les bibliothèques .NET de bonne qualité doivent s’efforcer de prendre en charge autant de plateformes et de développeurs que possible.</span><span class="sxs-lookup"><span data-stu-id="79a55-106">.NET runs in many places, and good .NET libraries should strive to support as many platforms and developers as possible.</span></span>

## <a name="strong-namingstrong-namingmd"></a>[<span data-ttu-id="79a55-107">Affectation de noms forts</span><span class="sxs-lookup"><span data-stu-id="79a55-107">Strong naming</span></span>](./strong-naming.md)

<span data-ttu-id="79a55-108">Découvrez l’affectation de noms forts, ses avantages et ses inconvénients.</span><span class="sxs-lookup"><span data-stu-id="79a55-108">Learn about strong naming and its advantages and disadvantages.</span></span> <span data-ttu-id="79a55-109">L’affectation d’un nom fort à une bibliothèque .NET permet à un maximum de développeurs de l’utiliser. En outre, c’est une pratique recommandée.</span><span class="sxs-lookup"><span data-stu-id="79a55-109">Strong naming a .NET library allows the most developers to use it and is a recommended best practice.</span></span>

## <a name="nuget-and-open-source-librariesnugetmd"></a>[<span data-ttu-id="79a55-110">Bibliothèques open source et NuGet</span><span class="sxs-lookup"><span data-stu-id="79a55-110">NuGet and open-source libraries</span></span>](./nuget.md)

<span data-ttu-id="79a55-111">La meilleure façon de créer des packages NuGet pour les bibliothèques .NET open source, notamment les métadonnées recommandées pour tous les packages publiés publiquement sur NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="79a55-111">The best way to create NuGet packages for open-source .NET libraries, including recommended metadata for all packages published publicly on NuGet.org.</span></span>

### <a name="dependenciesdependenciesmd"></a>[<span data-ttu-id="79a55-112">Dépendances</span><span class="sxs-lookup"><span data-stu-id="79a55-112">Dependencies</span></span>](./dependencies.md)

<span data-ttu-id="79a55-113">NuGet facilite l’utilisation des packages existants lors de la création d’une bibliothèque .NET.</span><span class="sxs-lookup"><span data-stu-id="79a55-113">NuGet makes it easy to use existing packages when building a .NET library.</span></span> <span data-ttu-id="79a55-114">Découvrez les sources courantes de friction entre les dépendances NuGet et comment les éviter.</span><span class="sxs-lookup"><span data-stu-id="79a55-114">Learn about NuGet dependencies' common sources of friction and how to avoid them.</span></span>

### <a name="sourcelinksourcelinkmd"></a>[<span data-ttu-id="79a55-115">SourceLink</span><span class="sxs-lookup"><span data-stu-id="79a55-115">SourceLink</span></span>](./sourcelink.md)

<span data-ttu-id="79a55-116">SourceLink est un excellent outil qui permet aux utilisateurs de votre bibliothèque .NET de parcourir son code source pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="79a55-116">SourceLink is a great tool that allows users of your .NET library to step into its source code while debugging.</span></span> <span data-ttu-id="79a55-117">Cet article est une vue d’ensemble de SourceLink et des raisons pour lesquelles vous devriez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="79a55-117">This article is an overview of what SourceLink is and why you should use it.</span></span>

### <a name="publishingpublish-nuget-packagemd"></a>[<span data-ttu-id="79a55-118">Publication</span><span class="sxs-lookup"><span data-stu-id="79a55-118">Publishing</span></span>](./publish-nuget-package.md)

<span data-ttu-id="79a55-119">Bien que NuGet.org soit le référentiel le plus largement connu et utilisé, il existe de nombreux endroits où publier des packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="79a55-119">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages.</span></span> <span data-ttu-id="79a55-120">Découvrez les différents référentiels de package NuGet disponibles et les meilleures pratiques de sécurité pour la publication d’une bibliothèque .NET.</span><span class="sxs-lookup"><span data-stu-id="79a55-120">Learn about the different NuGet package repositories available, and security best practices for publishing a .NET library.</span></span>

## <a name="versioningversioningmd"></a>[<span data-ttu-id="79a55-121">Gestion des versions</span><span class="sxs-lookup"><span data-stu-id="79a55-121">Versioning</span></span>](./versioning.md)

<span data-ttu-id="79a55-122">Les bonnes bibliothèques .NET évoluent au fil du temps, avec l’ajout de fonctionnalités, la résolution de bogues et l’amélioration des performances dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="79a55-122">Good .NET libraries evolve over time, adding features, fixing bugs, and improving performance in later releases.</span></span> <span data-ttu-id="79a55-123">Découvrez les différents numéros de version et comment communiquer les modifications avec rupture aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="79a55-123">Learn about the various version numbers and how to communicate breaking changes to developers.</span></span>

### <a name="breaking-changesbreaking-changesmd"></a>[<span data-ttu-id="79a55-124">Modifications avec rupture</span><span class="sxs-lookup"><span data-stu-id="79a55-124">Breaking changes</span></span>](./breaking-changes.md)

<span data-ttu-id="79a55-125">Il est important pour une bibliothèque .NET de trouver un équilibre entre la stabilité pour les utilisateurs existants et l’innovation pour l’avenir.</span><span class="sxs-lookup"><span data-stu-id="79a55-125">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="79a55-126">Découvrez les différents types de modifications avec rupture et de stratégies pour l’ajout de nouvelles fonctionnalités tout en conservant une compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="79a55-126">Learn about the different kinds of breaking changes and strategies for adding new features while maintaining backwards compatibility.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="79a55-127">[Précédent](./index.md)
[Suivant](./cross-platform-targeting.md)</span><span class="sxs-lookup"><span data-stu-id="79a55-127">[Previous](./index.md)
[Next](./cross-platform-targeting.md)</span></span>