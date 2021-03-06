---
title: Vue d'ensemble du composant ContextMenu
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746200"
---
# <a name="contextmenu-component-overview-windows-forms"></a>Vue d'ensemble du composant ContextMenu (Windows Forms)
> [!IMPORTANT]
> Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes, <xref:System.Windows.Forms.MainMenu> et les <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous le souhaitez.  
  
 Avec le composant Windows Forms <xref:System.Windows.Forms.ContextMenu>, vous pouvez fournir aux utilisateurs un menu contextuel facilement accessible des commandes fréquemment utilisées qui sont associées à l’objet sélectionné. Les éléments d’un menu contextuel sont souvent un sous-ensemble des éléments des menus principaux qui apparaissent ailleurs dans l’application. Un utilisateur peut généralement accéder à un menu contextuel en cliquant avec le bouton droit de la souris. Sur Windows Forms, les menus contextuels sont associés à des contrôles.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Vous pouvez associer un menu contextuel à un contrôle en affectant à la propriété <xref:System.Windows.Forms.Control.ContextMenu%2A> du contrôle la valeur du composant <xref:System.Windows.Forms.ContextMenu>. Un menu contextuel unique peut être associé à plusieurs contrôles, mais chaque contrôle ne peut avoir qu’un seul menu contextuel.  
  
 La propriété de clé du composant <xref:System.Windows.Forms.ContextMenu> est la propriété <xref:System.Windows.Forms.Menu.MenuItems%2A>. Vous pouvez ajouter des éléments de menu en créant par programmation des objets <xref:System.Windows.Forms.MenuItem> et en les ajoutant à la <xref:System.Windows.Forms.Menu.MenuItemCollection> du menu contextuel. Étant donné que les éléments d’un menu contextuel sont généralement dessinés à partir d’autres menus, vous pouvez ajouter des éléments à un menu contextuel en les copiant le plus souvent.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
