---
title: Exemples de scénarios d’entreprise et de cas d’utilisation pour les applications sans serveur
description: Découvrez sans serveur une approche pratique en accédant à des exemples qui vont du traitement d’image aux serveurs back-end mobiles et aux pipelines ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: adc4e1f3249cd72c423430ad4cb5dbb8eea8baf9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577282"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="37d80-103">Scénarios métier et cas d’usage serverless</span><span class="sxs-lookup"><span data-stu-id="37d80-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="37d80-104">Il existe de nombreux scénarios et scénarios d’utilisation pour les applications sans serveur.</span><span class="sxs-lookup"><span data-stu-id="37d80-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="37d80-105">Ce chapitre contient des exemples qui illustrent les différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="37d80-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="37d80-106">Les scénarios incluent des liens vers la documentation connexe et les référentiels de code source publics.</span><span class="sxs-lookup"><span data-stu-id="37d80-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="37d80-107">Les exemples de ce chapitre vous permettent de commencer à créer et à mettre en œuvre des solutions sans serveur.</span><span class="sxs-lookup"><span data-stu-id="37d80-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="analyze-and-archive-images"></a><span data-ttu-id="37d80-108">Analyser et archiver des images</span><span class="sxs-lookup"><span data-stu-id="37d80-108">Analyze and archive images</span></span>

<span data-ttu-id="37d80-109">Cet exemple illustre les événements sans serveur (Event Grid), les flux de travail (application logique) et le code (Azure Functions).</span><span class="sxs-lookup"><span data-stu-id="37d80-109">This sample demonstrates serverless events (Event Grid), workflows (Logic App), and code (Azure Functions).</span></span> <span data-ttu-id="37d80-110">Il montre également comment intégrer à une autre ressource, dans ce cas Cognitive Services pour l’analyse d’images.</span><span class="sxs-lookup"><span data-stu-id="37d80-110">It also shows how to integrate with another resource, in this case Cognitive Services for image analysis.</span></span>

<span data-ttu-id="37d80-111">Une application console vous permet de passer un lien vers une URL sur le Web.</span><span class="sxs-lookup"><span data-stu-id="37d80-111">A console application allows you to pass a link to a URL on the web.</span></span> <span data-ttu-id="37d80-112">L’application publie l’URL en tant que message de grille d’événements.</span><span class="sxs-lookup"><span data-stu-id="37d80-112">The app publishes the URL as an event grid message.</span></span> <span data-ttu-id="37d80-113">En parallèle, une application de fonction sans serveur et une application logique s’abonnent au message.</span><span class="sxs-lookup"><span data-stu-id="37d80-113">In parallel, a serverless function app and a logic app subscribe to the message.</span></span> <span data-ttu-id="37d80-114">L’application de fonction sans serveur sérialise l’image dans le stockage d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="37d80-114">The serverless function app serializes the image to blob storage.</span></span> <span data-ttu-id="37d80-115">Il stocke également des informations dans le stockage table Azure.</span><span class="sxs-lookup"><span data-stu-id="37d80-115">It also stores information in Azure Table Storage.</span></span> <span data-ttu-id="37d80-116">Les métadonnées stockent l’URL de l’image d’origine et le nom de l’image de l’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="37d80-116">The metadata stores the original image URL and the name of the blob image.</span></span> <span data-ttu-id="37d80-117">L’application logique interagit avec l’API Custom Vision pour analyser l’image et créer une légende générée par l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37d80-117">The logic app interacts with the Custom Vision API to analyze the image and create a machine-generated caption.</span></span> <span data-ttu-id="37d80-118">La légende est stockée dans la table de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="37d80-118">The caption is stored in the metadata table.</span></span>

![Analyser et archiver les images architecture](./media/image-processing-example.png)

<span data-ttu-id="37d80-120">Une application à page unique (SPA) distincte appelle une fonction sans serveur pour obtenir une liste d’images et de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="37d80-120">A separate single page application (SPA) calls a serverless function to get a list of images and metadata.</span></span> <span data-ttu-id="37d80-121">Pour chaque image, elle appelle une autre fonction qui remet les données de l’image à partir de l’archive.</span><span class="sxs-lookup"><span data-stu-id="37d80-121">For each image, it calls another function that delivers the image data from the archive.</span></span> <span data-ttu-id="37d80-122">Le résultat final est une galerie avec des légendes automatiques.</span><span class="sxs-lookup"><span data-stu-id="37d80-122">The final result is a gallery with automatic captions.</span></span>

![Galerie d’images automatisées](./media/automated-image-gallery.png)

<span data-ttu-id="37d80-124">Le référentiel complet et les instructions pour créer l’application logique sont disponibles ici: [Collage](https://github.com/JeremyLikness/Event-Grid-Glue)de la grille d’événements.</span><span class="sxs-lookup"><span data-stu-id="37d80-124">The full repository and instructions to build the logic app are available here: [Event grid glue](https://github.com/JeremyLikness/Event-Grid-Glue).</span></span>

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a><span data-ttu-id="37d80-125">Client mobile multiplateforme utilisant Xamarin. Forms et des fonctions</span><span class="sxs-lookup"><span data-stu-id="37d80-125">Cross-platform mobile client using Xamarin.Forms and functions</span></span>

<span data-ttu-id="37d80-126">Découvrez comment implémenter une fonction Azure simple sans serveur dans le portail Web Azure ou dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="37d80-126">See how to implement a simple serverless Azure Function in the Azure Web Portal or in Visual Studio.</span></span> <span data-ttu-id="37d80-127">Générez un client avec Xamarin. Forms qui s’exécute sur Android, iOS et Windows.</span><span class="sxs-lookup"><span data-stu-id="37d80-127">Build a client with Xamarin.Forms that runs on Android, iOS, and Windows.</span></span> <span data-ttu-id="37d80-128">L’application est ensuite affinée pour utiliser JavaScript Object Notation (JSON) comme un support de communication entre le serveur et les clients mobiles avec un back end sans serveur.</span><span class="sxs-lookup"><span data-stu-id="37d80-128">The application is then refined to use JavaScript Object Notation (JSON) as a communication medium between the server and the mobile clients with a serverless back end.</span></span>

<span data-ttu-id="37d80-129">Pour plus d’informations, consultez [implémentation d’une fonction Azure simple avec un client Xamarin. Forms.](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span><span class="sxs-lookup"><span data-stu-id="37d80-129">For more information, see [Implementing a simple Azure Function with a Xamarin.Forms client](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span></span>

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a><span data-ttu-id="37d80-130">Générer une mosaïque de photos avec reconnaissance d’image sans serveur</span><span class="sxs-lookup"><span data-stu-id="37d80-130">Generate a photo mosaic with serverless image recognition</span></span>

<span data-ttu-id="37d80-131">L’exemple utilise Azure Functions et Microsoft Cognitive Services Service Vision personnalisée pour générer une mosaïque de photos à partir d’une image d’entrée.</span><span class="sxs-lookup"><span data-stu-id="37d80-131">The sample uses Azure Functions and Microsoft Cognitive Services Custom Vision Service to generate a photo mosaic from an input image.</span></span> <span data-ttu-id="37d80-132">Le modèle est formé pour reconnaître les images.</span><span class="sxs-lookup"><span data-stu-id="37d80-132">The model is trained to recognize images.</span></span> <span data-ttu-id="37d80-133">Lorsqu’une image est téléchargée, elle reconnaît l’image et recherche avec Bing.</span><span class="sxs-lookup"><span data-stu-id="37d80-133">When an image is uploaded, it recognizes the image and searches with Bing.</span></span> <span data-ttu-id="37d80-134">L’image d’origine est recomposée à l’aide des résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="37d80-134">The original image is recomposed using the search results.</span></span>

![Photo et mosaïque de Orlando](./media/orlando-eye-both.png)

<span data-ttu-id="37d80-136">Par exemple, vous pouvez former votre modèle avec des points de vue Orlando, tels que l’œil-Orlando.</span><span class="sxs-lookup"><span data-stu-id="37d80-136">For example, you can train your model with Orlando landmarks, such as the Orlando Eye.</span></span> <span data-ttu-id="37d80-137">Custom Vision reconnaîtra une image de l’œil à Orlando, et la fonction créera une photo Mosaic composée de résultats de recherche d’images Bing pour «Orlando Eye».</span><span class="sxs-lookup"><span data-stu-id="37d80-137">Custom Vision will recognize an image of the Orlando Eye, and the function will create a photo mosaic composed of Bing image search results for "Orlando Eye."</span></span>

<span data-ttu-id="37d80-138">Pour plus d’informations, consultez [Azure Functions générateur](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)de mosaïques de photos.</span><span class="sxs-lookup"><span data-stu-id="37d80-138">For more information, see [Azure Functions photo mosaic generator](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).</span></span>

## <a name="migrate-an-existing-application-to-the-cloud"></a><span data-ttu-id="37d80-139">Migrer une application existante vers le Cloud</span><span class="sxs-lookup"><span data-stu-id="37d80-139">Migrate an existing application to the cloud</span></span>

<span data-ttu-id="37d80-140">Comme nous l’avons vu dans les chapitres précédents, il est courant d’adopter une architecture multiniveau pour héberger votre application en local.</span><span class="sxs-lookup"><span data-stu-id="37d80-140">As discussed in previous chapters, it's common to embrace an N-Tier architecture to host your application on-premises.</span></span> <span data-ttu-id="37d80-141">Bien que la migration des ressources «en l’or» à l’aide de machines virtuelles soit le chemin le moins risqué du Cloud, de nombreuses entreprises choisissent d’utiliser l’opportunité de refactoriser leurs applications.</span><span class="sxs-lookup"><span data-stu-id="37d80-141">Although migrating resources "as is" using virtual machines is the least risky path to the cloud, many companies choose to use the opportunity to refactor their applications.</span></span> <span data-ttu-id="37d80-142">Heureusement, la refactorisation ne doit pas nécessairement être un effort «tout ou rien».</span><span class="sxs-lookup"><span data-stu-id="37d80-142">Fortunately, refactoring doesn't have to be an "all-or-nothing" effort.</span></span> <span data-ttu-id="37d80-143">En fait, il est possible de migrer votre application, puis de remplacer les composants par fragments par des équivalents Cloud natifs.</span><span class="sxs-lookup"><span data-stu-id="37d80-143">In fact, it's possible to migrate your app then piecemeal replace components with cloud native counterparts.</span></span>

<span data-ttu-id="37d80-144">L’application utilise la fonctionnalité proxys de Azure Functions pour permettre la refactorisation d’un point de terminaison à partir d’un code local hérité vers un point de terminaison sans serveur.</span><span class="sxs-lookup"><span data-stu-id="37d80-144">The application uses the proxies feature of Azure Functions to enable refactoring an endpoint from legacy on-premises code to a serverless endpoint.</span></span>

![Architecture de la migration](./media/migration-architecture.png)

<span data-ttu-id="37d80-146">Le proxy fournit un point de terminaison d’API unique qui est mis à jour pour rediriger les demandes individuelles au fur et à mesure qu’elles sont déplacées dans des fonctions sans serveur.</span><span class="sxs-lookup"><span data-stu-id="37d80-146">The proxy provides a single API endpoint that is updated to reroute individual requests as they're moved into serverless functions.</span></span>

<span data-ttu-id="37d80-147">Vous pouvez afficher une vidéo qui vous guide tout au long de la migration: [Tirez et passez avec Azure Functions sans serveur](https://channel9.msdn.com/Events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="37d80-147">You can view a video that walks through the entire migration: [Lift and shift with serverless Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span> <span data-ttu-id="37d80-148">Accédez à l’exemple de code: [Apportez votre propre application](https://github.com/JeremyLikness/bring-own-app-connect-17).</span><span class="sxs-lookup"><span data-stu-id="37d80-148">Access the sample code: [Bring your own app](https://github.com/JeremyLikness/bring-own-app-connect-17).</span></span>

## <a name="parse-a-csv-file-and-insert-into-a-database"></a><span data-ttu-id="37d80-149">Analyser un fichier CSV et l’insérer dans une base de données</span><span class="sxs-lookup"><span data-stu-id="37d80-149">Parse a CSV file and insert into a database</span></span>

<span data-ttu-id="37d80-150">L’extraction, la transformation et le chargement (ETL) est une fonction métier courante qui intègre différents systèmes.</span><span class="sxs-lookup"><span data-stu-id="37d80-150">Extract, Transform, and Load (ETL) is a common business function that integrates different systems.</span></span> <span data-ttu-id="37d80-151">Les approches traditionnelles impliquent souvent la configuration de serveurs FTP dédiés, puis le déploiement de tâches planifiées pour analyser les fichiers et les traduire pour une utilisation professionnelle.</span><span class="sxs-lookup"><span data-stu-id="37d80-151">Traditional approaches often involve setting up dedicated FTP servers then deploying scheduled jobs to parse files and translate them for business use.</span></span> <span data-ttu-id="37d80-152">L’architecture sans serveur facilite le travail, car un déclencheur peut se déclencher lorsque le fichier est téléchargé.</span><span class="sxs-lookup"><span data-stu-id="37d80-152">Serverless architecture makes the job easier because a trigger can fire when the file is uploaded.</span></span> <span data-ttu-id="37d80-153">Azure Functions s’attaque à des tâches telles que ETL par le biais de sa composition idéale de petits morceaux de code qui se concentrent sur un problème spécifique.</span><span class="sxs-lookup"><span data-stu-id="37d80-153">Azure Functions tackles tasks like ETL through its ideal composition of small pieces of code that focus on a specific problem.</span></span>

![Capture d’écran montrant le processus d’analyse des volumes partagés de cluster.](./media/serverless-business-scenarios/csv-parse-database-import.png)

<span data-ttu-id="37d80-155">Pour obtenir le code source et un atelier pratique, consultez [laboratoire d’importation CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span><span class="sxs-lookup"><span data-stu-id="37d80-155">For source code and a hands-on lab, see [CSV import lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span></span>

## <a name="shorten-links-and-track-metrics"></a><span data-ttu-id="37d80-156">Raccourcissez les liens et suivez les mesures</span><span class="sxs-lookup"><span data-stu-id="37d80-156">Shorten links and track metrics</span></span>

<span data-ttu-id="37d80-157">Les outils de raccourci de liaison ont aidé à l’origine à coder les URL dans de courtes publications Twitter pour s’adapter à la limite de 140 caractères.</span><span class="sxs-lookup"><span data-stu-id="37d80-157">Link shortening tools originally helped encode URLs in short twitter posts to accommodate the 140 character limit.</span></span> <span data-ttu-id="37d80-158">Ils ont augmenté pour englober plusieurs utilisations, le plus souvent pour assurer le suivi des analyses.</span><span class="sxs-lookup"><span data-stu-id="37d80-158">They've grown to encompass several uses, most commonly to track click-throughs for analytics.</span></span> <span data-ttu-id="37d80-159">Le scénario Link raccourcisseur est une application entièrement sans serveur qui gère les liens et signale les métriques.</span><span class="sxs-lookup"><span data-stu-id="37d80-159">The link shortener scenario is an entirely serverless application that manages links and reports metrics.</span></span>

<span data-ttu-id="37d80-160">Azure Functions est utilisé pour traiter une application à page unique (SPA) qui vous permet de coller l’URL longue et de générer des URL courtes.</span><span class="sxs-lookup"><span data-stu-id="37d80-160">Azure Functions is used to serve a Single Page Application (SPA) that allows you to paste the long URL and generate short URLs.</span></span> <span data-ttu-id="37d80-161">Les URL sont marquées pour effectuer le suivi des éléments tels que des campagnes (rubriques) et des supports (tels que les réseaux sociaux dans lesquels les liens sont publiés).</span><span class="sxs-lookup"><span data-stu-id="37d80-161">The URLs are tagged to track things like campaigns (topics) and mediums (such as social networks that the links are posted to).</span></span> <span data-ttu-id="37d80-162">Le code bref est stocké dans le stockage table Azure comme clé, avec l’URL longue comme valeur.</span><span class="sxs-lookup"><span data-stu-id="37d80-162">The short code is stored in Azure Table Storage as the key, with the long URL as the value.</span></span> <span data-ttu-id="37d80-163">Lorsque vous cliquez sur le lien Short, une autre fonction recherche l’URL longue, envoie une redirection et place des informations sur l’événement dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="37d80-163">When you click on the short link, another function looks up the long URL, sends a redirect, and places information about the event on a queue.</span></span> <span data-ttu-id="37d80-164">Une autre fonction Azure traite la file d’attente et place les informations dans Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="37d80-164">Another Azure Function processes the queue and places the information into Azure Cosmos DB.</span></span>

![Lier l’architecture raccourcisseur](./media/link-shortener-architecture.png)

<span data-ttu-id="37d80-166">Vous pouvez ensuite créer un tableau de bord Power BI pour collecter des informations sur les données collectées.</span><span class="sxs-lookup"><span data-stu-id="37d80-166">You can then create a Power BI dashboard to gather insights about the data collected.</span></span> <span data-ttu-id="37d80-167">Sur la back end, Application Insights fournit des mesures importantes.</span><span class="sxs-lookup"><span data-stu-id="37d80-167">On the back end, Application Insights provides important metrics.</span></span> <span data-ttu-id="37d80-168">La télémétrie comprend le temps nécessaire à la redirection de l’utilisateur moyen et le temps nécessaire pour accéder au stockage table Azure.</span><span class="sxs-lookup"><span data-stu-id="37d80-168">Telemetry includes how long it takes for the average user to redirect and how long it takes to access Azure Table Storage.</span></span>

![Exemple de Power BI](./media/power-bi-example.png)

<span data-ttu-id="37d80-170">Le dépôt Raccourcisseur de liens complet avec des instructions est disponible ici: [URL sans serveur raccourcisseur](https://github.com/jeremylikness/serverless-url-shortener).</span><span class="sxs-lookup"><span data-stu-id="37d80-170">The full link shortener repository with instructions is available here: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener).</span></span> <span data-ttu-id="37d80-171">Vous pouvez en savoir plus sur une version simplifiée ici: [Stockage Azure pour les applications .net sans serveur en quelques minutes](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).</span><span class="sxs-lookup"><span data-stu-id="37d80-171">You can read about a simplified version here: [Azure Storage for serverless .NET apps in minutes](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).</span></span>

## <a name="verify-device-connectivity-using-a-ping"></a><span data-ttu-id="37d80-172">Vérifier la connectivité de l’appareil à l’aide d’une commande ping</span><span class="sxs-lookup"><span data-stu-id="37d80-172">Verify device connectivity using a ping</span></span>

<span data-ttu-id="37d80-173">L’exemple se compose d’une IoT Hub Azure et d’une fonction Azure.</span><span class="sxs-lookup"><span data-stu-id="37d80-173">The sample consists of an Azure IoT Hub and an Azure Function.</span></span> <span data-ttu-id="37d80-174">Un nouveau message sur le IoT Hub déclenche la fonction Azure.</span><span class="sxs-lookup"><span data-stu-id="37d80-174">A new message on the IoT Hub triggers the Azure Function.</span></span> <span data-ttu-id="37d80-175">Le code sans serveur renvoie le même contenu de message à l’appareil qui l’a envoyé.</span><span class="sxs-lookup"><span data-stu-id="37d80-175">The serverless code sends the same message content back to the device that sent it.</span></span> <span data-ttu-id="37d80-176">Le projet dispose de tout le code et de la configuration de déploiement requis pour la solution.</span><span class="sxs-lookup"><span data-stu-id="37d80-176">The project has all the code and deployment configuration needed for the solution.</span></span>

<span data-ttu-id="37d80-177">Pour plus d’informations, consultez [Azure IOT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).</span><span class="sxs-lookup"><span data-stu-id="37d80-177">For more information, see [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="37d80-178">Ressources recommandées</span><span class="sxs-lookup"><span data-stu-id="37d80-178">Recommended resources</span></span>

* [<span data-ttu-id="37d80-179">Générateur de mosaïque de photos Azure Functions</span><span class="sxs-lookup"><span data-stu-id="37d80-179">Azure Functions photo mosaic generator</span></span>](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [<span data-ttu-id="37d80-180">Test ping Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="37d80-180">Azure IoT Hub ping</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [<span data-ttu-id="37d80-181">Stockage Azure pour les applications .NET sans serveur en quelques minutes</span><span class="sxs-lookup"><span data-stu-id="37d80-181">Azure Storage for serverless .NET apps in minutes</span></span>](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [<span data-ttu-id="37d80-182">Apporter votre propre application</span><span class="sxs-lookup"><span data-stu-id="37d80-182">Bring your own app</span></span>](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [<span data-ttu-id="37d80-183">Laboratoire d’importation CSV</span><span class="sxs-lookup"><span data-stu-id="37d80-183">CSV import lab</span></span>](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [<span data-ttu-id="37d80-184">Collage dans la grille d’événements</span><span class="sxs-lookup"><span data-stu-id="37d80-184">Event grid glue</span></span>](https://github.com/JeremyLikness/Event-Grid-Glue)
* [<span data-ttu-id="37d80-185">Implémentation d’une fonction Azure simple avec un client Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="37d80-185">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [<span data-ttu-id="37d80-186">Tirez et passez avec Azure Functions sans serveur</span><span class="sxs-lookup"><span data-stu-id="37d80-186">Lift and shift with serverless Azure functions</span></span>](https://channel9.msdn.com/Events/Connect/2017/E102)
* [<span data-ttu-id="37d80-187">URL sans serveur raccourcisseur</span><span class="sxs-lookup"><span data-stu-id="37d80-187">Serverless URL shortener</span></span>](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
><span data-ttu-id="37d80-188">[Précédent](orchestration-patterns.md)
>[Suivant](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="37d80-188">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>