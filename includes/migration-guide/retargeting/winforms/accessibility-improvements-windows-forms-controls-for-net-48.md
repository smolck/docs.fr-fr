---
ms.openlocfilehash: 140a9044b553a008112af93efb8eeba2bf3b07cb
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440264"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a><span data-ttu-id="a6129-101">Améliorations des fonctionnalités d’accessibilité dans les contrôles Windows Forms pour .NET 4.8</span><span class="sxs-lookup"><span data-stu-id="a6129-101">Accessibility improvements in Windows Forms controls for .NET 4.8</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a6129-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a6129-102">Details</span></span>|<span data-ttu-id="a6129-103">Windows Forms Framework continue d’améliorer la façon dont il utilise les technologies d’accessibilité pour mieux répondre aux besoins de ses clients.</span><span class="sxs-lookup"><span data-stu-id="a6129-103">The Windows Forms Framework is continuing to improve how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="a6129-104">Citons notamment les changements suivants :</span><span class="sxs-lookup"><span data-stu-id="a6129-104">These include the following changes:</span></span><ul><li><span data-ttu-id="a6129-105">Changements visant à améliorer l’affichage en mode Contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="a6129-105">Changes to improve display during High Contrast mode.</span></span></li><li><span data-ttu-id="a6129-106">Changements apportés à l’interaction avec le Narrateur.</span><span class="sxs-lookup"><span data-stu-id="a6129-106">Changes to interaction with Narrator.</span></span></li><li><span data-ttu-id="a6129-107">Changements dans la hiérarchie accessible (amélioration de la navigation dans l’arborescence UI Automation).</span><span class="sxs-lookup"><span data-stu-id="a6129-107">Changes in the Accessible hierarchy (improving navigation through the UI Automation tree).</span></span></li></ul>|
|<span data-ttu-id="a6129-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a6129-108">Suggestion</span></span>|<span data-ttu-id="a6129-109"><strong>Comment accepter ou refuser ces changements</strong>Pour tirer parti de ces changements, l’application doit s’exécuter sur .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="a6129-109"><strong>How to opt in or out of these changes</strong>In order for the application to benefit from these changes, it must run on the .NET Framework 4.8.</span></span> <span data-ttu-id="a6129-110">Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6129-110">The application can opt in into these changes in either of the following ways:</span></span><ul><li><span data-ttu-id="a6129-111">Recompilez-la pour qu’elle cible .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="a6129-111">It is recompiled to target the .NET Framework 4.8.</span></span> <span data-ttu-id="a6129-112">Ces changements d’accessibilité sont activés par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="a6129-112">These accessibility changes are enabled by default on Windows Forms applications that target the .NET Framework 4.8.</span></span></li><li><span data-ttu-id="a6129-113">Faites-lui cibler .NET Framework version 4.7.2 ou antérieure et cessez d’adhérer aux comportements d’accessibilité existants, en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant dans la section <code>&lt;runtime&gt;</code> du fichier de configuration de l’application et en lui affectant la valeur <code>false</code>, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a6129-113">It targets the .NET Framework 4.7.2 or earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>, as the following example shows.</span></span></li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="a6129-114">Notez que pour adhérer aux fonctionnalités d’accessibilité ajoutées à .NET Framework 4.8, vous devez également adhérer aux fonctionnalités d’accessibilité de .NET Framework 4.7.1 et 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="a6129-114">Note that to opt in to the accessibility features added in .NET Framework 4.8, you must also opt in to accessibility features of .NET Framework 4.7.1 and 4.7.2 as well.</span></span> <span data-ttu-id="a6129-115">Si vos applications ciblent .NET Framework 4.8 et que vous souhaitez conserver le comportement d’accessibilité existant, choisissez d’adhérer aux fonctionnalités d’accessibilité existantes en affectant explicitement à ce commutateur AppContext la valeur <code>true</code>. L’activation de la prise en charge de l’appel des info-bulles au clavier demande d’ajouter la ligne <code>Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false</code> à la valeur AppContextSwitchOverrides :</span><span class="sxs-lookup"><span data-stu-id="a6129-115">Applications that target the .NET Framework 4.8 and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to <code>true</code>.Enabling the keyboard ToolTip invocation support requires adding the <code>Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false</code> line to the AppContextSwitchOverrides value:</span></span><pre><code class="lang-xml">&#39;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false&quot; /&gt;&#39;&#13;&#10;</code></pre><span data-ttu-id="a6129-116">Notez que l’activation de cette fonctionnalité demande d’adhérer aux fonctionnalités d’accessibilité susmentionnées de .NET Framework 4.7.1 - 4.8.</span><span class="sxs-lookup"><span data-stu-id="a6129-116">Note that enabling this feature requires opting in to the aforementioned accessibility features of .NET Framework 4.7.1 - 4.8.</span></span> <span data-ttu-id="a6129-117">De plus, si vous n’avez pas adhéré à l’une des fonctionnalités d’accessibilité mais que l’info-bulle affiche le contraire, une <xref:System.NotSupportedException> d’exécution est levée la première fois que vous accédez à ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="a6129-117">Also, if any of the accessibility features are not opted in but the tooltip display feature is opted in, a runtime <xref:System.NotSupportedException> will be thrown on the first access to these features.</span></span> <span data-ttu-id="a6129-118">Le message de l’exception indique que les info-bulles au clavier nécessitent que les améliorations de l’accessibilité de niveau 3 soient activées. <strong>Utilisation des couleurs définies par le système d’exploitation dans les thèmes à contraste élevé</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-118">The exception message indicates that keyboard ToolTips require accessibility improvements of level 3 to be enabled.<strong>Use of OS-defined colors in High Contrast themes</strong></span></span><ul><li><span data-ttu-id="a6129-119">Thèmes à contraste élevé améliorés.</span><span class="sxs-lookup"><span data-stu-id="a6129-119">Improved high-contrast themes.</span></span></li></ul><span data-ttu-id="a6129-120"><strong>Prise en charge améliorée du Narrateur</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-120"><strong>Improved Narrator support</strong></span></span><ul><li><span data-ttu-id="a6129-121">Le Narrateur annonce désormais le sens du tri de la <xref:System.Windows.Forms.DataGridViewColumn> quand il annonce un nom accessible d’une <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="a6129-121">Narrator now announces the sort direction of the <xref:System.Windows.Forms.DataGridViewColumn> when announcing an accessible name of a <xref:System.Windows.Forms.DataGridViewCell>.</span></span></li></ul><span data-ttu-id="a6129-122"><strong>Prise en charge améliorée de l’accessibilité de CheckedListBox</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-122"><strong>Improved CheckedListBox Accessibility support</strong></span></span><ul><li><span data-ttu-id="a6129-123">Prise en charge améliorée du Narrateur pour le contrôle <xref:System.Windows.Forms.CheckedListBox>.</span><span class="sxs-lookup"><span data-stu-id="a6129-123">Improved Narrator support for the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> <span data-ttu-id="a6129-124">Quand vous accédez au contrôle <xref:System.Windows.Forms.CheckedListBox> à l’aide du clavier, le Narrateur se focalise sur l’élément <xref:System.Windows.Forms.CheckedListBox> et l’annonce.</span><span class="sxs-lookup"><span data-stu-id="a6129-124">When navigating to the <xref:System.Windows.Forms.CheckedListBox> control using the keyboard, Narrator focuses the <xref:System.Windows.Forms.CheckedListBox> item and announces it.</span></span></li><li><span data-ttu-id="a6129-125">Un contrôle CheckedListBox vide a maintenant un rectangle dessiné pour un premier élément virtuel quand le contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="a6129-125">An empty CheckedListBox control now has a focus rectangle drawn for a virtual first item when the control becomes focused.</span></span></li></ul><span data-ttu-id="a6129-126"><strong>Prise en charge améliorée de l’accessibilité de ComboBox</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-126"><strong>Improved ComboBox Accessibility support</strong></span></span><ul><li><span data-ttu-id="a6129-127">Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.ComboBox>, avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.</span><span class="sxs-lookup"><span data-stu-id="a6129-127">Enabled UI Automation support for the <xref:System.Windows.Forms.ComboBox> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span></li></ul><span data-ttu-id="a6129-128"><strong>Prise en charge améliorée de l’accessibilité dans un DataGridView</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-128"><strong>Improved DataGridView Accessibility support</strong></span></span><ul><li><span data-ttu-id="a6129-129">Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.DataGridView> avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.</span><span class="sxs-lookup"><span data-stu-id="a6129-129">Enabled UI Automation support for <xref:System.Windows.Forms.DataGridView> control with ability to use UI Automation notifications and other UI Automation features.</span></span></li><li><span data-ttu-id="a6129-130">L’élément UI Automation qui correspond au <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> ou au <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> est maintenant un enfant de la cellule d’édition correspondante.</span><span class="sxs-lookup"><span data-stu-id="a6129-130">The UI Automation element which corresponds to the <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> or <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> is now a child of corresponding editing cell.</span></span></li></ul><span data-ttu-id="a6129-131"><strong>Prise en charge améliorée de l’accessibilité de LinkLabel</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-131"><strong>Improved LinkLabel Accessibility support</strong></span></span><ul><li><span data-ttu-id="a6129-132">Amélioration de l’accessibilité du contrôle <xref:System.Windows.Forms.LinkLabel> : Le Narrateur annonce l’état désactivé du lien si le contrôle <xref:System.Windows.Forms.LinkLabel> correspondant est désactivé.</span><span class="sxs-lookup"><span data-stu-id="a6129-132">Improved <xref:System.Windows.Forms.LinkLabel> control accessibility: Narrator announces the disabled state for the link if the corresponding <xref:System.Windows.Forms.LinkLabel> control is disabled.</span></span></li></ul><span data-ttu-id="a6129-133"><strong>Prise en charge améliorée de l’accessibilité de ProgressBar</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-133"><strong>Improved ProgressBar Accessibility support</strong></span></span><ul><li><span data-ttu-id="a6129-134">Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.ProgressBar> avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.</span><span class="sxs-lookup"><span data-stu-id="a6129-134">Enabled UI Automation support for the <xref:System.Windows.Forms.ProgressBar> control with the ability to use UI Automation notifications and other UI Automation features.</span></span> <span data-ttu-id="a6129-135">Les développeurs peuvent maintenant utiliser les notifications UI Automation que le Narrateur peut annoncer pour indiquer la progression.</span><span class="sxs-lookup"><span data-stu-id="a6129-135">Developers are now able to use UI Automation notifications which Narrator can announce to indicate progress.</span></span></li></ul><span data-ttu-id="a6129-136">Pour une vue d’ensemble des événements UI Automation, notamment les événements de notification UI Automation, consultez la [Vue d’ensemble des événements UI Automation](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview).<strong>Prise en charge améliorée de l’accessibilité de PropertyGrid</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-136">For an overview of UI automation events overview, including UI automation notification events, see the [UI Automation Events Overview](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview).<strong>Improved PropertyGrid Accessibility support</strong></span></span><ul><li><span data-ttu-id="a6129-137">Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.PropertyGrid>, avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.</span><span class="sxs-lookup"><span data-stu-id="a6129-137">Enabled UI Automation support for the <xref:System.Windows.Forms.PropertyGrid> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span></li><li><span data-ttu-id="a6129-138">L’élément UI Automation qui correspond à la propriété en cours de modification est maintenant un enfant de l’élément UI Automation de l’élément de propriété correspondant.</span><span class="sxs-lookup"><span data-stu-id="a6129-138">The UI Automation element which corresponds to the currently edited property is now a child of the corresponding property item UI Automation element.</span></span></li><li><span data-ttu-id="a6129-139">L’élément de l’élément de propriété UI Automation est maintenant un enfant de l’élément de catégorie correspondant si le contrôle <xref:System.Windows.Forms.PropertyGrid> parent est défini sur la vue des catégories.</span><span class="sxs-lookup"><span data-stu-id="a6129-139">The UI Automation property item element is now a child of the corresponding category element if the parent <xref:System.Windows.Forms.PropertyGrid> control is set to category view.</span></span></li></ul><span data-ttu-id="a6129-140"><strong>Prise en charge améliorée de ToolStrip</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-140"><strong>Improved ToolStrip support</strong></span></span><ul><li><span data-ttu-id="a6129-141">Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.ToolStrip>, avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.</span><span class="sxs-lookup"><span data-stu-id="a6129-141">Enabled UI Automation support for the <xref:System.Windows.Forms.ToolStrip> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span></li><li><span data-ttu-id="a6129-142">Amélioration de la navigation des éléments <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a6129-142">Improved navigation through <xref:System.Windows.Forms.ToolStrip> items.</span></span></li><li><span data-ttu-id="a6129-143">En mode Éléments, le focus du Narrateur ne disparaît pas et ne va pas vers les éléments masqués.</span><span class="sxs-lookup"><span data-stu-id="a6129-143">In items mode, Narrator focus does not disappear and does not go to hidden items.</span></span></li></ul><span data-ttu-id="a6129-144"><strong>Amélioration des indices visuels</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-144"><strong>Improved Visual cues</strong></span></span><ul><li><span data-ttu-id="a6129-145">Un contrôle <xref:System.Windows.Forms.CheckedListBox> vide affiche maintenant un indicateur de focus quand il reçoit le focus.</span><span class="sxs-lookup"><span data-stu-id="a6129-145">An empty <xref:System.Windows.Forms.CheckedListBox> control now displays a focus indicator when it receives focus.</span></span></li></ul><span data-ttu-id="a6129-146">Remarque : La prise en charge de UI Automation est activée pour les contrôles au moment du runtime, mais n’est pas utilisée au moment du design.</span><span class="sxs-lookup"><span data-stu-id="a6129-146">Note: UI automation support is enabled for controls in runtime but is not used in design time.</span></span> <span data-ttu-id="a6129-147">Pour une vue d’ensemble d’UI Automation, consultez la [Vue d’ensemble d’UI Automation](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span><span class="sxs-lookup"><span data-stu-id="a6129-147">For an overview of UI automation, see the [UI Automation Overview](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span></span></p><span data-ttu-id="a6129-148"><strong>Appel des info-bulles des contrôles au clavier</strong></span><span class="sxs-lookup"><span data-stu-id="a6129-148"><strong>Invoking controls' ToolTips with a keyboard</strong></span></span><ul><li><span data-ttu-id="a6129-149">Maintenant, vous pouvez utiliser le clavier pour appeler les info-bulles des contrôles en mettant le focus sur le contrôle souhaité.</span><span class="sxs-lookup"><span data-stu-id="a6129-149">Control tooltip can now be invoked by focusing the control with keyboard.</span></span> <span data-ttu-id="a6129-150">Cette fonctionnalité doit être activée explicitement pour l’application (voir la section <strong>&quot;Comment accepter ou refuser ces changements&quot;</strong>)</span><span class="sxs-lookup"><span data-stu-id="a6129-150">This feature needs to be enabled explicitly for the application (see section <strong>&quot;How to opt in or out of these changes&quot;</strong>)</span></span></li></ul>|
|<span data-ttu-id="a6129-151">Portée</span><span class="sxs-lookup"><span data-stu-id="a6129-151">Scope</span></span>|<span data-ttu-id="a6129-152">Majeur</span><span class="sxs-lookup"><span data-stu-id="a6129-152">Major</span></span>|
|<span data-ttu-id="a6129-153">Version</span><span class="sxs-lookup"><span data-stu-id="a6129-153">Version</span></span>|<span data-ttu-id="a6129-154">4.8</span><span class="sxs-lookup"><span data-stu-id="a6129-154">4.8</span></span>|
|<span data-ttu-id="a6129-155">Type</span><span class="sxs-lookup"><span data-stu-id="a6129-155">Type</span></span>|<span data-ttu-id="a6129-156">Reciblage</span><span class="sxs-lookup"><span data-stu-id="a6129-156">Retargeting</span></span>|