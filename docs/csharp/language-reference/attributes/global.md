---
title: 'Attributs réservés CMD : attributs mondiaux'
ms.date: 04/09/2020
description: Les attributs fournissent des métadonnées que le compilateur utilise pour comprendre plus de sémantique de votre programme
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389855"
---
# <a name="reserved-attributes-assembly-level-attributes"></a><span data-ttu-id="4c3f0-103">Attributs réservés : attributs de niveau d’assemblage</span><span class="sxs-lookup"><span data-stu-id="4c3f0-103">Reserved attributes: Assembly level attributes</span></span>

<span data-ttu-id="4c3f0-104">La plupart des attributs sont appliqués à des éléments de langage spécifiques, tels que les classes ou les méthodes. Toutefois, certains attributs sont globaux : ils s’appliquent à la totalité d’un assembly ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-104">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="4c3f0-105">Par exemple, l’attribut <xref:System.Reflection.AssemblyVersionAttribute> peut être utilisé pour incorporer des informations de version dans un assembly, de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="4c3f0-105">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

<span data-ttu-id="4c3f0-106">Les attributs globaux apparaissent dans le `using` code source après toutes les directives de haut niveau et avant tout type, module ou déclarations d’espace de nom.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-106">Global attributes appear in the source code after any top level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="4c3f0-107">Les attributs globaux peuvent apparaître dans plusieurs fichiers sources, mais les fichiers doivent être compilés en un seul passage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-107">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="4c3f0-108">Visual Studio ajoute des attributs globaux au fichier AssemblyInfo.cs dans les projets cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-108">Visual Studio adds global attributes to the AssemblyInfo.cs file in .NET Framework projects.</span></span> <span data-ttu-id="4c3f0-109">Ces attributs ne sont pas ajoutés aux projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-109">These attributes aren't added to .NET Core projects.</span></span>

<span data-ttu-id="4c3f0-110">Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-110">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="4c3f0-111">Ils sont répartis dans les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c3f0-111">They fall into the following categories:</span></span>

- <span data-ttu-id="4c3f0-112">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="4c3f0-112">Assembly identity attributes</span></span>
- <span data-ttu-id="4c3f0-113">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="4c3f0-113">Informational attributes</span></span>
- <span data-ttu-id="4c3f0-114">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="4c3f0-114">Assembly manifest attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="4c3f0-115">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="4c3f0-115">Assembly identity attributes</span></span>

<span data-ttu-id="4c3f0-116">Trois attributs (avec un nom fort, le cas échéant), déterminent l’identité d’un assembly : nom, version et culture.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-116">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="4c3f0-117">Ces attributs constituent le nom complet de l’assembly et sont obligatoires quand vous le référencez le code.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-117">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="4c3f0-118">Vous pouvez définir la version et la culture d’un assembly en utilisant des attributs.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-118">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="4c3f0-119">Cependant, la valeur du nom est définie par le compilateur, le Visual Studio IDE dans la [boîte de dialogue d’information d’assemblage](/visualstudio/ide/reference/assembly-information-dialog-box), ou le Lien d’assemblage (Al.exe) lors de la création de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-119">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created.</span></span> <span data-ttu-id="4c3f0-120">Le nom de l’assemblée est basé sur le manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-120">The assembly name is based on the assembly manifest.</span></span> <span data-ttu-id="4c3f0-121">L’attribut <xref:System.Reflection.AssemblyFlagsAttribute> spécifie si plusieurs copies de l’assembly peuvent coexister.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-121">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="4c3f0-122">Le tableau suivant présente les attributs d’identité.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-122">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="4c3f0-123">Attribut</span><span class="sxs-lookup"><span data-stu-id="4c3f0-123">Attribute</span></span>|<span data-ttu-id="4c3f0-124">Objectif</span><span class="sxs-lookup"><span data-stu-id="4c3f0-124">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="4c3f0-125">Spécifie la version d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-125">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="4c3f0-126">Spécifie la culture prise en charge par l'assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-126">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="4c3f0-127">Spécifie si un assembly prend en charge l’exécution côte à côte sur le même ordinateur, dans le même processus ou dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-127">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

## <a name="informational-attributes"></a><span data-ttu-id="4c3f0-128">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="4c3f0-128">Informational attributes</span></span>

<span data-ttu-id="4c3f0-129">Vous utilisez des attributs d’information pour fournir des informations supplémentaires sur l’entreprise ou le produit d’un assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-129">You use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="4c3f0-130">Le tableau suivant présente les attributs d’informations définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-130">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="4c3f0-131">Attribut</span><span class="sxs-lookup"><span data-stu-id="4c3f0-131">Attribute</span></span>|<span data-ttu-id="4c3f0-132">Objectif</span><span class="sxs-lookup"><span data-stu-id="4c3f0-132">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="4c3f0-133">Spécifie un nom de produit pour un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-133">Specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="4c3f0-134">Spécifie une marque de commerce pour un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-134">Specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="4c3f0-135">Spécifie une version d’information pour un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-135">Specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="4c3f0-136">Spécifie un nom d’entreprise pour un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-136">Specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="4c3f0-137">Définit un attribut personnalisé qui spécifie un copyright pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-137">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="4c3f0-138">Définit un numéro de version spécifique pour la ressource de version de fichier Win32.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-138">Sets a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="4c3f0-139">Indique si l’assembly est conforme à la spécification CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="4c3f0-139">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="4c3f0-140">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="4c3f0-140">Assembly manifest attributes</span></span>

<span data-ttu-id="4c3f0-141">Vous pouvez utiliser les attributs de manifeste de l’assembly pour fournir des informations dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-141">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="4c3f0-142">Les attributs incluent le titre, la description, l’alias par défaut et la configuration.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-142">The attributes include title, description, default alias, and configuration.</span></span> <span data-ttu-id="4c3f0-143">Le tableau suivant présente les attributs de manifeste de l’assembly définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-143">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="4c3f0-144">Attribut</span><span class="sxs-lookup"><span data-stu-id="4c3f0-144">Attribute</span></span>|<span data-ttu-id="4c3f0-145">Objectif</span><span class="sxs-lookup"><span data-stu-id="4c3f0-145">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="4c3f0-146">Spécifie un titre d’assemblage pour un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-146">Specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="4c3f0-147">Spécifie une description d’assemblage pour un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-147">Specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="4c3f0-148">Spécifie une configuration d’assemblage (comme la vente au détail ou le débogé) pour un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-148">Specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="4c3f0-149">Définit un alias par défaut convivial pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3f0-149">Defines a friendly default alias for an assembly manifest</span></span>|