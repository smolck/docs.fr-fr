---
title: Débogage de flux de travail
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 2bfc50215697636f1771d6bb35510fbf9e0b435d
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802633"
---
# <a name="debugging-workflows"></a>Débogage de flux de travail

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] offre plusieurs options permettant de déboguer des workflows en cours d'exécution à partir de l'environnement de développement. Les workflows peuvent être débogués dans le concepteur, dans XAML et dans le code.

## <a name="debugging-in-the-workflow-designer"></a>Débogage dans le concepteur de workflow

Les points d’arrêt peuvent être définis sur des activités dans le concepteur de flux de travail en mettant en surbrillance l’activité et en appuyant sur <kbd>F9</kbd> ou en utilisant le menu contextuel de l’activité. Ainsi, l'exécution du workflow s'arrête lorsque l'hôte de workflow est exécuté en mode débogage. Dans la capture d'écran suivante, l'exécution du workflow est suspendue à un point d'arrêt. Pour plus d’informations, consultez [débogage de flux de travail avec l’Concepteur de flux de travail](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).

## <a name="debugging-in-xaml"></a>Débogage dans XAML

Si un workflow a suspendu son exécution à un point d'arrêt dans le concepteur, le workflow peut également être débogué dans XAML. Pour afficher le point d’exécution en XAML, sélectionnez **vue XAML** dans le concepteur de workflow lorsque l’exécution du workflow est suspendue. Il est possible de revenir au mode de débogage dans le concepteur de workflow en rouvrant le workflow dans le concepteur à partir de l'Explorateur de solutions. Pour plus d’informations, consultez [Comment : déboguer du code XAML avec l’Concepteur de flux de travail](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).

## <a name="debugging-in-code"></a>Débogage dans le code

Pour définir un point d’arrêt, cliquez sur la marge de gauche du volet de code ou appuyez sur <kbd>F9</kbd> avec le curseur sur la ligne où vous souhaitez le définir.

## <a name="attaching-to-a-workflow-process"></a>Attachement à un processus de workflow

Le débogage de workflow permet également d'utiliser l'infrastructure de Visual Studio pour attacher un processus. Cela permet à l'auteur de workflow de déboguer un workflow qui est exécuté dans un environnement hôte différent, tel qu'Internet Information Services 7.0 (IIS).

## <a name="remote-debugging"></a>Remote Debugging

Les fonctions de débogage à distance Windows Workflow Foundation (WF) sont identiques au débogage à distance pour d’autres composants de Visual Studio. Pour plus d’informations sur l’utilisation du débogage à distance, consultez [Comment : activer le débogage distant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

> [!NOTE]
> Si l’application de workflow cible l’architecture x86 et est hébergée sur un ordinateur exécutant un système d’exploitation 64 bits, le débogage à distance ne fonctionnera pas, sauf si Visual Studio est installé sur l’ordinateur distant ou si la cible de l’application de workflow est remplacée par **n’importe quel processeur**.

## <a name="extending-the-workflow-debugging-service"></a>Extension du service de débogage de workflow

Le service de débogage de workflow est maintenant public et peut être utilisé pour créer des applications personnalisées, notamment pour la surveillance, la simulation et le débogage dans un concepteur réhébergé. Pour plus d'informations, voir l'article <xref:System.Activities.Presentation.Debug.DebuggerService>.
