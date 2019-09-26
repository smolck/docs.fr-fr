---
title: Éblouissant pour les développeurs ASP.NET Web Forms
description: Découvrez comment créer des applications Web à pile complète avec .NET à l’aide de éblouissant et de .NET Core de manière simple et familière.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: a80483f6a1f1cb9e5a3e2ffff18cbd59c5b67af3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183797"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a><span data-ttu-id="1527c-103">Éblouissant pour les développeurs ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="1527c-103">Blazor for ASP.NET Web Forms Developers</span></span>

![Capture d’écran montrant la couverture du livre électronique Applications serverless.](./media/index/blazor-for-web-forms-developers-cover.png)

> <span data-ttu-id="1527c-105">TÉLÉCHARGEMENT disponible à l’adresse suivante : <https://aka.ms/blazor-ebook></span><span class="sxs-lookup"><span data-stu-id="1527c-105">DOWNLOAD available at: <https://aka.ms/blazor-ebook></span></span>

<span data-ttu-id="1527c-106">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="1527c-106">PUBLISHED BY</span></span>

<span data-ttu-id="1527c-107">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1527c-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="1527c-108">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1527c-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="1527c-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="1527c-109">One Microsoft Way</span></span>

<span data-ttu-id="1527c-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="1527c-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="1527c-111">Copyright © 2019 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1527c-111">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="1527c-112">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="1527c-112">All rights reserved.</span></span> <span data-ttu-id="1527c-113">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="1527c-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="1527c-114">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="1527c-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="1527c-115">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="1527c-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="1527c-116">Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs.</span><span class="sxs-lookup"><span data-stu-id="1527c-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="1527c-117">Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.</span><span class="sxs-lookup"><span data-stu-id="1527c-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="1527c-118">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1527c-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="1527c-119">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="1527c-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="1527c-120">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="1527c-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="1527c-121">Extrait</span><span class="sxs-lookup"><span data-stu-id="1527c-121">Authors:</span></span>

> <span data-ttu-id="1527c-122">**[Daniel Roth](https://github.com/danroth27)** , responsable de programme principal, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="1527c-122">**[Daniel Roth](https://github.com/danroth27)**, Principal Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="1527c-123">**[Jeff Fritz](https://github.com/csharpfritz)** , responsable de programme senior, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="1527c-123">**[Jeff Fritz](https://github.com/csharpfritz)**, Senior Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="1527c-124">**[Taylor Southwick](https://github.com/twsouthwick)** , ingénieur logiciel senior, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="1527c-124">**[Taylor Southwick](https://github.com/twsouthwick)**, Senior Software Engineer, Microsoft Corp.</span></span>

> <span data-ttu-id="1527c-125">**[Scott Addie](https://github.com/scottaddie)** , développeur de contenu senior, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="1527c-125">**[Scott Addie](https://github.com/scottaddie)**, Senior Content Developer, Microsoft Corp.</span></span>

## <a name="introduction"></a><span data-ttu-id="1527c-126">Introduction</span><span class="sxs-lookup"><span data-stu-id="1527c-126">Introduction</span></span>

<span data-ttu-id="1527c-127">.NET offre un développement d’applications Web long pris en charge via ASP.NET, un ensemble complet d’infrastructures et d’outils permettant de créer n’importe quel type d’application Web.</span><span class="sxs-lookup"><span data-stu-id="1527c-127">.NET has long supported web app development through ASP.NET, a comprehensive set of frameworks and tools for building any kind of web app.</span></span> <span data-ttu-id="1527c-128">ASP.NET a son propre lignage de frameworks et de technologies Web en commençant par les pages ASP (Classic Active Server Pages).</span><span class="sxs-lookup"><span data-stu-id="1527c-128">ASP.NET has its own lineage of web frameworks and technologies starting all the way back with classic Active Server Pages (ASP).</span></span> <span data-ttu-id="1527c-129">Les infrastructures comme ASP.NET Web Forms, ASP.NET MVC, pages Web ASP.NET et les ASP.NET Core plus récentes offrent un moyen productif et puissant de créer des applications Web de *type serveur* , où le contenu de l’interface utilisateur est généré dynamiquement sur le serveur en réponse à http obtenteur.</span><span class="sxs-lookup"><span data-stu-id="1527c-129">Frameworks like ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages, and more recently ASP.NET Core, provide a productive and powerful way to build *server-rendered* web apps, where UI content is dynamically generated on the server in response to HTTP requests.</span></span> <span data-ttu-id="1527c-130">Chaque Framework ASP.NET répond à un public et une philosophie de construction d’applications différents.</span><span class="sxs-lookup"><span data-stu-id="1527c-130">Each ASP.NET framework caters to a different audience and app building philosophy.</span></span> <span data-ttu-id="1527c-131">ASP.NET Web Forms fourni avec la version d’origine du .NET Framework et du développement Web activé à l’aide de nombreux modèles familiers pour les développeurs de bureau, comme les contrôles d’interface utilisateur réutilisables avec une gestion des événements simple.</span><span class="sxs-lookup"><span data-stu-id="1527c-131">ASP.NET Web Forms shipped with the original release of the .NET Framework and enabled web development using many of the patterns familiar to desktop developers, like reusable UI controls with simple event handling.</span></span> <span data-ttu-id="1527c-132">Toutefois, aucune des offres ASP.NET ne permet d’exécuter du code qui s’exécute dans le navigateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1527c-132">However, none of the ASP.NET offerings provide a way to run code that executed in the user's browser.</span></span> <span data-ttu-id="1527c-133">Pour ce faire, il est nécessaire d’écrire du code JavaScript et d’utiliser l’un des nombreux frameworks et outils JavaScript qui ont été mis en avant et non en popularité au fil des années : jQuery, Knockout, angulaire, REACT, etc.</span><span class="sxs-lookup"><span data-stu-id="1527c-133">To do that requires writing JavaScript and using any of the many JavaScript frameworks and tools that have phased in and out of popularity over the years: jQuery, Knockout, Angular, React, and so on.</span></span>

<span data-ttu-id="1527c-134">[Éblouissant](https://blazor.net) est une nouvelle infrastructure Web qui change ce qui est possible lors de la création d’applications Web avec .net.</span><span class="sxs-lookup"><span data-stu-id="1527c-134">[Blazor](https://blazor.net) is a new web framework that changes what is possible when building web apps with .NET.</span></span> <span data-ttu-id="1527c-135">Éblouissant est une infrastructure d’interface utilisateur Web côté client basée sur C# au lieu de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="1527c-135">Blazor is a client-side web UI framework based on C# instead of JavaScript.</span></span> <span data-ttu-id="1527c-136">Avec éblouissant, vous pouvez écrire vos composants de logique et d’interface utilisateur côté C#client dans, les compiler dans des assemblys .NET normaux, puis les exécuter directement dans le navigateur à l’aide d’une nouvelle norme Web ouverte appelée webassembly.</span><span class="sxs-lookup"><span data-stu-id="1527c-136">With Blazor you can write your client-side logic and UI components in C#, compile them into normal .NET assemblies, and then run them directly in the browser using a new open web standard called WebAssembly.</span></span> <span data-ttu-id="1527c-137">Ou bien, éblouissant peut exécuter vos composants de l’interface utilisateur .NET sur le serveur et gérer les interactions de l’interface utilisateur de manière fluide sur une connexion en temps réel avec le navigateur.</span><span class="sxs-lookup"><span data-stu-id="1527c-137">Or alternatively, Blazor can run your .NET UI components on the server and handle all UI interactions fluidly over a real-time connection with the browser.</span></span> <span data-ttu-id="1527c-138">Lorsqu’il est associé à .NET en cours d’exécution sur le serveur, éblouissant permet le développement Web à pile complète avec .NET.</span><span class="sxs-lookup"><span data-stu-id="1527c-138">When paired with .NET running on the server, Blazor enables full-stack web development with .NET.</span></span> <span data-ttu-id="1527c-139">Bien que éblouissant partage de nombreux points communs avec ASP.NET Web Forms, comme le fait de disposer d’un modèle de composant réutilisable et d’un moyen simple de gérer les événements utilisateur, il s’appuie également sur les fondations de .NET Core pour offrir une expérience de développement Web moderne et hautes performances.</span><span class="sxs-lookup"><span data-stu-id="1527c-139">While Blazor shares many commonalities with ASP.NET Web Forms, like having a reusable component model and a simple way to handle user events, it also builds on the foundations of .NET Core to provide a modern and high performance web development experience.</span></span>

<span data-ttu-id="1527c-140">Cet ouvrage présente ASP.NET Web Forms les développeurs à éblouissant de manière familière et pratique.</span><span class="sxs-lookup"><span data-stu-id="1527c-140">This book introduces ASP.NET Web Forms developers to Blazor in a way that is familiar and convenient.</span></span> <span data-ttu-id="1527c-141">Il présente des concepts éblouissants en parallèle avec des concepts analogues dans ASP.NET Web Forms tout en expliquant les nouveaux concepts qui peuvent être moins familiers.</span><span class="sxs-lookup"><span data-stu-id="1527c-141">It introduces Blazor concepts in parallel with analogous concepts in ASP.NET Web Forms while also explaining new concepts that may be less familiar.</span></span> <span data-ttu-id="1527c-142">Il couvre un large éventail de sujets et de préoccupations, notamment la création de composants, le routage, la disposition, la configuration et la sécurité.</span><span class="sxs-lookup"><span data-stu-id="1527c-142">It covers a broad range of topics and concerns including component authoring, routing, layout, configuration, and security.</span></span> <span data-ttu-id="1527c-143">Et si le contenu de ce livre est principalement destiné à l’activation d’un nouveau développement, il couvre également des instructions et des stratégies pour la migration de ASP.NET existant Web Forms vers éblouissant pour le moment où vous souhaitez moderniser une application existante.</span><span class="sxs-lookup"><span data-stu-id="1527c-143">And while the content of this book is primarily for enabling new development, it also covers guidelines and strategies for migrating existing ASP.NET Web Forms to Blazor for when you want to modernize an existing app.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="1527c-144">Qui doit utiliser le livre</span><span class="sxs-lookup"><span data-stu-id="1527c-144">Who should use the book</span></span>

<span data-ttu-id="1527c-145">Ce livre est destiné aux développeurs ASP.NET Web Forms qui recherchent une introduction à éblouissant qui se réfère à leurs connaissances et compétences existantes.</span><span class="sxs-lookup"><span data-stu-id="1527c-145">This book is for ASP.NET Web Forms developers looking for an introduction to Blazor that relates to their existing knowledge and skills.</span></span> <span data-ttu-id="1527c-146">Ce livre peut vous aider à prendre rapidement en main un nouveau projet basé sur éblouissant ou à représenter un plan pour la modernisation d’une application ASP.NET Web Forms existante.</span><span class="sxs-lookup"><span data-stu-id="1527c-146">This book can help with quickly getting started on a new Blazor-based project or to help chart a roadmap for modernizing an existing ASP.NET Web Forms application.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="1527c-147">Comment utiliser le livre</span><span class="sxs-lookup"><span data-stu-id="1527c-147">How to use the book</span></span>

<span data-ttu-id="1527c-148">La première partie de ce livre couvre ce qu’est le plus éblouissant et le compare au développement d’applications Web avec ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="1527c-148">The first part of this book covers what Blazor is and compares it to web app development with ASP.NET Web Forms.</span></span> <span data-ttu-id="1527c-149">Le livre aborde ensuite un large éventail de sujets éblouissants, le chapitre par chapitre, et met en relation chaque concept éblouissant avec le concept correspondant dans ASP.NET Web Forms, ou il décrit entièrement tout un ensemble de concepts.</span><span class="sxs-lookup"><span data-stu-id="1527c-149">The book then covers a variety of Blazor topics, chapter by chapter, and relates each Blazor concept to the corresponding concept in ASP.NET Web Forms, or explains fully any completely new concepts.</span></span> <span data-ttu-id="1527c-150">Le livre fait également référence régulièrement à un exemple d’application complet implémenté à la fois dans ASP.NET Web Forms et éblouissant pour illustrer les fonctionnalités éblouissantes et fournir une étude de cas pour la migration de ASP.NET Web Forms vers éblouissant.</span><span class="sxs-lookup"><span data-stu-id="1527c-150">The book also refers regularly to a complete sample app implemented in both ASP.NET Web Forms and Blazor to demonstrate Blazor features and to provide a case study for migrating from ASP.NET Web Forms to Blazor.</span></span> <span data-ttu-id="1527c-151">Vous trouverez les deux implémentations de l’exemple d’application (ASP.NET Web Forms et des versions de éblouissant) sur [GitHub](https://github.com/dotnet-architecture/eshoponblazor).</span><span class="sxs-lookup"><span data-stu-id="1527c-151">You can find both implementations of the sample app (ASP.NET Web Forms and Blazor versions) on [GitHub](https://github.com/dotnet-architecture/eshoponblazor).</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="1527c-152">Ce que ce livre ne couvre pas</span><span class="sxs-lookup"><span data-stu-id="1527c-152">What this book doesn't cover</span></span>

<span data-ttu-id="1527c-153">Ce livre est une introduction à éblouissant, pas un guide de migration complet.</span><span class="sxs-lookup"><span data-stu-id="1527c-153">This book is an introduction to Blazor, not a comprehensive migration guide.</span></span> <span data-ttu-id="1527c-154">Bien qu’il inclue des conseils sur la façon d’aborder la migration d’un projet de ASP.NET Web Forms vers éblouissant, il n’essaie pas de couvrir toutes les nuances et tous les détails.</span><span class="sxs-lookup"><span data-stu-id="1527c-154">While it does include guidance on how to approach migrating a project from ASP.NET Web Forms to Blazor, it does not attempt to cover every nuance and detail.</span></span> <span data-ttu-id="1527c-155">Pour plus d’informations générales sur la migration de ASP.NET vers ASP.NET Core, reportez-vous aux [instructions de migration](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) dans la documentation ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="1527c-155">For more general guidance on migrating from ASP.NET to ASP.NET Core, refer to the [migration guidance](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) in the ASP.NET Core documentation.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1527c-156">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1527c-156">Additional resources</span></span>

<span data-ttu-id="1527c-157">Vous trouverez la page d’hébergement et la documentation de éblouissants <https://blazor.net>sur le.</span><span class="sxs-lookup"><span data-stu-id="1527c-157">You can find the official Blazor home page and documentation at <https://blazor.net>.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="1527c-158">Envoyez votre feedback</span><span class="sxs-lookup"><span data-stu-id="1527c-158">Send your feedback</span></span>

<span data-ttu-id="1527c-159">Ce livre et les exemples associés sont en constante évolution. vos commentaires sont donc accueillis !</span><span class="sxs-lookup"><span data-stu-id="1527c-159">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="1527c-160">Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section commentaires au bas de toute page reposant sur les [problèmes GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="1527c-160">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="1527c-161">Next</span><span class="sxs-lookup"><span data-stu-id="1527c-161">Next</span></span>](introduction.md)