---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643983"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. DoNotLoadLatestRichEditControl non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyImages`, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Modifier la description

Dans le .NET Framework 4.6.2 et les versions antérieures, le contrôle <xref:System.Windows.Forms.RichTextBox> instancie le contrôle Win32 RichEdit v 3.0 et, pour les applications qui ciblent .NET Framework 4.7.1, le contrôle <xref:System.Windows.Forms.RichTextBox> instancie RichEdit v 4.1 (dans *que dans msftedit. dll*). Le commutateur de compatibilité `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` a été introduit pour permettre aux applications qui ciblent .NET Framework 4.7.1 et versions ultérieures de refuser le nouveau contrôle RichEdit v 4.1 et d’utiliser à la place l’ancien contrôle RichEdit v3.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` n’est pas pris en charge. Seules les nouvelles versions du contrôle <xref:System.Windows.Forms.RichTextBox> sont prises en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->