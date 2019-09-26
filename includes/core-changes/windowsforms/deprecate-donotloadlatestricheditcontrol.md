---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181796"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="77e8e-101">Commutateur de compatibilité Switch. System. Windows. Forms. DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="77e8e-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="77e8e-102">Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e8e-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="77e8e-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="77e8e-103">Change description</span></span>

<span data-ttu-id="77e8e-104">Dans le .NET Framework 4.6.2 et les versions antérieures, <xref:System.Windows.Forms.RichTextBox> le contrôle instancierait le contrôle Win32 RichEdit v 3.0 et, pour les applications qui ciblent .NET Framework <xref:System.Windows.Forms.RichTextBox> 4.7.1, le contrôle instancierait RichEdit v 4.1 (dans  *que dans msftedit. dll*).</span><span class="sxs-lookup"><span data-stu-id="77e8e-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="77e8e-105">Le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur de compatibilité a été introduit pour permettre aux applications qui ciblent .NET Framework 4.7.1 et versions ultérieures de refuser le nouveau contrôle RichEdit v 4.1 et d’utiliser à la place l’ancien contrôle RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="77e8e-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="77e8e-106">Dans .net Core, le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="77e8e-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="77e8e-107">Seules les <xref:System.Windows.Forms.RichTextBox> nouvelles versions du contrôle sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="77e8e-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="77e8e-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="77e8e-108">Version introduced</span></span>

<span data-ttu-id="77e8e-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="77e8e-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="77e8e-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="77e8e-110">Recommended action</span></span>

<span data-ttu-id="77e8e-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="77e8e-111">Remove the switch.</span></span> <span data-ttu-id="77e8e-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="77e8e-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="77e8e-113">Category</span><span class="sxs-lookup"><span data-stu-id="77e8e-113">Category</span></span>

<span data-ttu-id="77e8e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="77e8e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="77e8e-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="77e8e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->