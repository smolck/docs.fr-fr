---
title: XAML Namespaces et Namespace Mapping
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
ms.openlocfilehash: 9b01643e8f8d77073595253580ebea60fabfd23b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186232"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Espaces de noms XAML et mappage d'espace de noms pour XAML WPF
Cette rubrique explique plus en détail la présence et la finalité des deux mappages d’espace de noms XAML qui figurent souvent dans la balise racine de chaque fichier XAML WPF. Elle décrit également comment produire des mappages similaires pour utiliser des éléments définis dans votre propre code et/ou dans des assemblys distincts.  

## <a name="what-is-a-xaml-namespace"></a>Qu’est-ce qu’un espace de noms XAML ?  
 Un espace de noms XAML est en réalité une extension du concept d’espace de noms XML. Les techniques de spécification d’un espace de noms XAML reposent sur la syntaxe d’espace de noms XML, la convention de l’utilisation d’URI comme identificateurs d’espaces de noms, à l’aide de préfixes permettant de fournir un moyen de référencer plusieurs espaces de noms à partir de la même source de balise, et ainsi de suite. Le concept principal de la définition XAML de l’espace de noms XML est qu’un espace de noms XAML implique une portée d’unicité pour les utilisations de balisage et qu’il influence également la façon dont les entités de balisage sont potentiellement associées aux espaces de noms CLR spécifiques et aux assemblys référencés. Cette dernière considération est également influencée par le concept d’un contexte de schéma XAML. Pour comprendre comment WPF fonctionne avec les espaces de noms XAML, imaginez les espaces de noms XAML en termes d’espaces de noms XAML par défaut, d’espace de noms de langage XAML et tout espace de noms XAML supplémentaire mappé directement par votre balisage XAML aux espaces de noms CLR de stockage spécifiques et assemblys référencés.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a>Déclarations des espaces de noms XAML et WPF  
 Il y a généralement deux déclarations d’espaces de noms XML dans les déclarations d’espace de noms figurant dans la balise racine de nombreux fichiers XAML. La première déclaration mappe l’espace de noms XAML général du client ou du framework WPF comme valeur par défaut :  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 La deuxième déclaration mappe (généralement) un espace de noms XAML distinct au préfixe `x:`.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 La relation entre ces déclarations est la suivante : le mappage du préfixe `x:` prend en charge les intrinsèques qui font partie de la définition de langage XAML ; [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est une implémentation qui utilise XAML comme langage et définit un vocabulaire de ses objets pour XAML. Étant donné que les utilisations du vocabulaire WPF sont beaucoup plus courantes que les utilisations des intrinsèques XAML, le vocabulaire WPF est mappé comme valeur par défaut.  
  
 La `x:` convention de préfixe pour cartographier le support intrinsèque de langue XAML est suivie par des modèles de projet, le code d’échantillon, et la documentation des dispositifs linguistiques dans ce SDK. L’espace de noms XAML définit de nombreuses fonctions courantes qui sont nécessaires, notamment pour les applications WPF de base. Par exemple, pour joindre tout code-behind à un fichier XAML par le biais d’une classe partielle, vous devez nommer cette classe comme attribut `x:Class` dans l’élément racine du fichier XAML approprié. Ou bien, tout élément tel qu’il est défini dans une page XAML à laquelle vous souhaitez accéder comme une ressource à clé doit avoir l’attribut `x:Key` défini par l’élément en question. Pour plus d’informations sur ces questions et d’autres aspects du langage XAML, consultez [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) ou [Syntaxe XAML en détail](xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mappage aux classes et assemblys personnalisés  
 Vous pouvez mapper des espaces de noms XML à des assemblys à l’aide d’une série de jetons dans une déclaration de préfixe `xmlns`, de la même manière que les espaces de noms XAML WPF et XAML intrinsèques standard sont mappés aux préfixes.  
  
 La syntaxe prend les valeurs et les jetons nommés possibles suivants :  
  
 `clr-namespace:` Espace de noms CLR déclaré dans l’assembly contenant les types publics à exposer comme éléments.  
  
 `assembly=`L’assemblage qui contient une partie ou la totalité de l’espace de nom CLR référencé. En général, cette valeur est simplement le nom de l’assembly, pas le chemin, et n’inclut pas l’extension (comme .dll ou .exe). Le chemin à cet assembly doit être établi comme référence de projet dans le fichier projet qui contient le XAML que vous essayez de mapper. Afin d’incorporer la version et la `assembly` signature de nom fort, la valeur peut être une chaîne telle que définie par <xref:System.Reflection.AssemblyName>, plutôt que le nom de chaîne simple.  
  
 Notez que le jeton `clr-namespace` est séparé de sa valeur par deux-points (:), alors que le caractère qui sépare le jeton `assembly` de sa valeur est le signe égal (=). Le caractère à utiliser entre ces deux jetons est un point-virgule. En outre, n’incluez aucun espace blanc n’importe où dans la déclaration.  
  
### <a name="a-basic-custom-mapping-example"></a>Exemple de mappage personnalisé de base  
 Le code suivant définit un exemple de classe personnalisée :  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 Cette classe personnalisée est ensuite compilée dans une bibliothèque qui, conformément aux paramètres du projet (non affichés), est nommée `SDKSampleLibrary`.  
  
 Pour référencer cette classe personnalisée, vous devez également l’inclure comme référence pour votre projet actuel, comme vous le feriez à l’aide de l’interface utilisateur de l’Explorateur de solutions dans Visual Studio.  
  
 Maintenant que vous avez une bibliothèque qui contient une classe, ainsi qu’une référence à cette bibliothèque dans les paramètres du projet, vous pouvez ajouter le mappage de préfixe suivant comme élément de votre élément racine dans le code XAML :  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Pour résumer, le code suivant est du code XAML qui inclut le mappage personnalisé avec la valeur par défaut typique et les mappages x: dans la balise racine, puis utilise une référence préfixée pour instancier `ExampleClass` dans cette interface utilisateur :  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a>Mappage aux assemblys actuels  
 `assembly` peut être omis si le `clr-namespace` référencé est défini dans le même assembly que le code d’application qui fait référence aux classes personnalisées. Une syntaxe équivalente dans ce cas consiste à spécifier `assembly=`, sans jeton de chaîne après le signe égal.  
  
 Les classes personnalisées ne peuvent pas être utilisées comme élément racine d’une page si elles sont définies dans le même assembly. Les classes partielles ne doivent pas être mappées ; seules les classes qui ne sont pas la classe partielle d’une page dans votre application doivent être mappées si vous prévoyez de les référencer comme éléments dans le code XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Mappage d’espaces de noms CLR à des espaces de noms XML dans un assembly  
 WPF définit un attribut CLR qui est consommé par les processeurs XAML pour mapper plusieurs espaces de noms CLR à un espace de noms XAML unique. Cet attribut, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, est placé au niveau de l’assemblage dans le code source qui produit l’assemblage. Le code source d’assemblage WPF utilise cet attribut pour <xref:System.Windows> <xref:System.Windows.Controls>cartographier `http://schemas.microsoft.com/winfx/2006/xaml/presentation` les différents espaces de noms communs, tels que et , à l’espace nom.  
  
 Le <xref:System.Windows.Markup.XmlnsDefinitionAttribute> prend deux paramètres: le nom XML/XAML namespace, et le nom CLR namespace. Plus d’un <xref:System.Windows.Markup.XmlnsDefinitionAttribute> peut exister pour cartographier plusieurs espaces de noms CLR à la même espace de nom XML. Une fois mappés, les membres de ces espaces de noms peuvent également être référencés sans qualification complète, si vous le souhaitez, en fournissant l’instruction `using` appropriée dans la page code-behind de la classe partielle. Pour plus d'informations, consultez <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Espaces de noms concepteurs et autres préfixes de modèles XAML  
 Si vous travaillez avec les environnements de développement et/ou les outils de conception pour XAML WPF, vous remarquerez peut-être qu’il existe d’autres espaces de noms/préfixes XAML définis dans le balisage XAML.  
  
 WPF Designer for Visual Studio utilise un namespace de `d:`concepteur qui est généralement cartographié sur le préfixe . Des modèles de projet plus récents pour WPF pourraient pré-cartographier cet espace de nom XAML pour soutenir l’échange de la XAML entre WPF Designer pour Visual Studio et d’autres environnements de conception. Cet espace de noms de conception XAML permet de perpétuer l’état de conception pendant les allers-retours de l’interface utilisateur basée sur XAML dans le concepteur. Il est également utilisé pour les fonctionnalités telles que `d:IsDataSource`, qui activent des sources de données du runtime dans un concepteur.  
  
 Un autre préfixe que vous pouvez voir mappé est `mc:`. `mc:` est destiné à la compatibilité du balisage et exploite un modèle de compatibilité du balisage qui n’est pas nécessairement spécifique au XAML. Dans une certaine mesure, les fonctionnalités de compatibilité du balisage peuvent être utilisées pour échanger XAML entre les frameworks ou sur d’autres limites d’implémentation de stockage pour travailler entre des contextes de schémas XAML, fournir la compatibilité pour des modes limités dans les concepteurs, etc. Pour plus d’informations sur les concepts de compatibilité du balisage et leurs rapports à WPF, consultez [Fonctionnalités de langage pour la compatibilité du balisage (mc:)](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF et chargement des assemblys  
 Le contexte schéma XAML pour WPF s’intègre au modèle d’application WPF, <xref:System.AppDomain>qui utilise à son tour le concept défini par CLR de . La séquence suivante décrit comment le contexte du schéma XAML interprète comment charger des assemblages ou trouver <xref:System.AppDomain> des types au moment de l’exécution ou au moment de la conception, en fonction de l’utilisation de WPF et d’autres facteurs.  
  
1. Itérer à <xref:System.AppDomain>travers le , à la recherche d’un assemblage déjà chargé qui correspond à tous les aspects du nom, à partir de l’assemblage le plus récemment chargé.  
  
2. Si le nom est <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> qualifié, faites appel au nom qualifié.  
  
3. Si combinaison nom court + jeton de clé publique d’un nom qualifié correspond à l’assembly à partir duquel le balisage a été chargé, retournez cet assembly.  
  
4. Utilisez le nom court et le <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>jeton de clé publique pour appeler .  
  
5. Si le nom n’est <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>pas qualifié, appelez .  
  
 Le XAML libre n’utilise pas l’étape 3 ; il n’y a pas de chargement à partir de l’assembly.  
  
 Compilé XAML pour WPF (généré via XamlBuildTask) n’utilise <xref:System.AppDomain> pas les assemblages déjà chargés à partir de (Étape 1). En outre, le nom ne doit jamais être non qualifié à partir de la sortie de XamlBuildTask ; donc l’étape 5 ne s’applique pas.  
  
 Le BAML compilé (généré par l’intermédiaire de PresentationBuildTask) utilise toutes les étapes, bien que le BAML ne doit pas contenir de noms d’assembly non qualifiés.  
  
## <a name="see-also"></a>Voir aussi

- [Présentation des espaces de noms XML](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
