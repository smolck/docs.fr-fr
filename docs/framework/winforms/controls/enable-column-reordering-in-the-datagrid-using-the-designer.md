---
title: Activer la réorganisation des colonnes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 14dc1081a8608c6e6add67f641c4b55825d2fc81
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626969"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>Comment : activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur
Lorsque vous affichez les données affichées dans un contrôle de <xref:System.Windows.Forms.DataGridView> Windows Forms, les utilisateurs souhaitent parfois comparer les valeurs de colonnes spécifiques. Cela peut être gênant si les colonnes sont très éloignées dans le contrôle, en particulier si les utilisateurs doivent faire défiler horizontalement vers l’avant pour voir toutes les colonnes qui les intéressent. Vous pouvez faciliter la comparaison des valeurs de colonne en permettant à vos utilisateurs de réorganiser les colonnes. Lorsque vous activez la réorganisation des colonnes, les utilisateurs peuvent déplacer une colonne vers une nouvelle position en faisant glisser l’en-tête de colonne avec la souris.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-enable-column-reordering"></a>Pour activer la réorganisation des colonnes

- Cliquez sur le glyphe actions du concepteur (![petite flèche noire](./media/designer-actions-glyph.gif)) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **activer la réorganisation des colonnes**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Guide pratique pour figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md)
