---
title: Code source L2DBForm.xaml.cs
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 882699a76eab3c291cd92c298287bc5d28fb08e1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920859"
---
# <a name="l2dbformxamlcs-source-code"></a>Code source L2DBForm.xaml.cs

Cette page contient le contenu et la description du C# code source dans le fichier *L2DBForm.Xaml.cs*. La classe partielle L2XDBForm contenue dans ce fichier peut être divisée en trois sections logiques : les membres de données et les gestionnaires d'événements de clic sur le bouton `OnRemove` et `OnAddBook`.

## <a name="data-members"></a>Membres de données

Deux membres de données privés sont utilisés pour associer cette classe aux ressources de fenêtre utilisées dans *L2DBForm.xaml*.

- La variable d'espace de noms `myBooks` est initialisée à `"http://www.mybooks.com"`.

- Le membre `bookList` est initialisé dans le constructeur à la chaîne CDATA dans *L2DBForm.xaml* avec la ligne suivante :

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>Gestionnaire d’événements OnAddBook

Cette méthode contient les trois instructions suivantes :

- La première instruction conditionnelle est utilisée pour la validation d’entrée.

- La deuxième instruction crée un nouveau <xref:System.Xml.Linq.XElement> à partir des valeurs de chaîne que l’utilisateur a entrées dans la section d’interface utilisateur **Add New Book**.

- La dernière instruction ajoute ce nouvel élément au fournisseur de données dans *L2DBForm.xaml*. En conséquence, la liaison de données dynamiques mettra automatiquement à jour l'interface utilisateur avec ce nouvel élément ; aucun code supplémentaire fourni par l'utilisateur n'est nécessaire.

## <a name="onremove-event-handler"></a>Gestionnaire d’événements OnRemove

Le gestionnaire `OnRemove` est plus complexe que le gestionnaire `OnAddBook` pour deux raisons. Tout d'abord, le code XML brut contenant des espaces conservés, les nouvelles lignes correspondantes doivent également être supprimées avec l'entrée de livre. Ensuite, pour plus de commodité, la sélection (qui était sur l'élément supprimé) est réinitialisée à l'élément précédent dans la liste.

Toutefois, le travail principal lié à la suppression de l’élément de livre sélectionné est effectué par deux instructions uniquement :

- Tout d'abord, l'élément de livre associé à l'élément actuellement sélectionné dans la zone de liste est récupéré :

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- Ensuite, cet élément est supprimé du fournisseur de données :

    ```csharp
    selBook.Remove();
    ```

Là encore, la liaison de données dynamiques s'assure que l'interface utilisateur du programme est mise à jour automatiquement.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a>Comments

Pour obtenir la source XAML associée pour ces gestionnaires, consultez [Code source de L2DBForm.xaml](l2dbform-xaml-source-code.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : exemple LinqToXmlDataBinding](linq-to-xml-data-binding-sample.md)
- [Code source L2DBForm.xaml](l2dbform-xaml-source-code.md)
