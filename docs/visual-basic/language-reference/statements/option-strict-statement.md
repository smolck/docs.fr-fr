---
title: Option Strict Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: a002526a107fdc6e8e02890d11db94a3d224c94b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353762"
---
# <a name="option-strict-statement"></a>Option Strict Statement
Restreint les conversions de types de données implicites aux conversions étendues, interdit la liaison tardive et interdit le typage implicite qui produit un type de `Object`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`On`|Ce paramètre est facultatif. Active la vérification de `Option Strict`.|  
|`Off`|Ce paramètre est facultatif. Désactive la vérification de la `Option Strict`.|  
  
## <a name="remarks"></a>Notes  
 Lorsque `Option Strict On` ou `Option Strict` apparaît dans un fichier, les conditions suivantes provoquent une erreur au moment de la compilation :  
  
- Conversions restrictives implicites  
  
- Liaison tardive  
  
- Saisie implicite qui génère un type `Object`  
  
> [!NOTE]
> Dans les configurations d’avertissement que vous pouvez définir sur la [page compiler, le concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), il existe trois paramètres qui correspondent aux trois conditions qui provoquent une erreur au moment de la compilation. Pour plus d’informations sur l’utilisation de ces paramètres, consultez [pour définir des configurations d’avertissement dans l’IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) plus loin dans cette rubrique.  
  
 L’instruction `Option Strict Off` désactive la vérification des erreurs et des avertissements pour les trois conditions, même si les paramètres IDE associés spécifient d’activer ces erreurs ou avertissements. L’instruction `Option Strict On` active la vérification des erreurs et des avertissements pour les trois conditions, même si les paramètres IDE associés spécifient de désactiver ces erreurs ou avertissements.  
  
 Si elle est utilisée, l’instruction `Option Strict` doit apparaître avant toute autre instruction de code dans un fichier.  
  
 Lorsque vous affectez à `Option Strict` la valeur `On`, Visual Basic vérifie que les types de données sont spécifiés pour tous les éléments de programmation. Les types de données peuvent être spécifiés explicitement ou spécifiés à l’aide de l’inférence de type local. Il est recommandé de spécifier des types de données pour tous vos éléments de programmation, pour les raisons suivantes :  
  
- Il permet la prise en charge d’IntelliSense pour vos variables et paramètres. Cela vous permet de voir leurs propriétés et d’autres membres au fur et à mesure que vous tapez du code.  
  
- Elle permet au compilateur d’effectuer une vérification de type. La vérification de type vous aide à trouver les instructions qui peuvent échouer au moment de l’exécution en raison d’erreurs de conversion de type. Il identifie également les appels aux méthodes sur les objets qui ne prennent pas en charge ces méthodes.  
  
- Elle accélère l’exécution du code. Cela est dû au fait que si vous ne spécifiez pas de type de données pour un élément de programmation, le compilateur Visual Basic lui assigne le type de `Object`. Le code compilé peut être obligé de passer de la `Object` à d’autres types de données, ce qui réduit les performances.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Erreurs de conversion restrictive implicite  
 Les erreurs de conversion restrictive implicite se produisent quand une conversion de types de données implicite est une conversion restrictive.  
  
 Visual Basic pouvez convertir de nombreux types de données en d’autres types de données. Une perte de données peut se produire lorsque la valeur d’un type de données est convertie en un type de données ayant une précision moindre ou une capacité inférieure. Une erreur d’exécution se produit si une telle conversion restrictive échoue. `Option Strict` garantit la notification au moment de la compilation de ces conversions restrictives afin que vous puissiez les éviter. Pour plus d’informations, consultez [conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) et [conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Les conversions qui peuvent provoquer des erreurs incluent les conversions implicites qui se produisent dans les expressions. Pour plus d’informations, consultez les rubriques suivantes :  
  
- [+, opérateur](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+=, opérateur](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/=, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char (type de données)](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Lorsque vous concaténez des chaînes à l’aide de l' [opérateur &](../../../visual-basic/language-reference/operators/concatenation-operator.md), toutes les conversions en chaînes sont considérées comme étendues. Par conséquent, ces conversions ne génèrent pas d’erreur de conversion restrictive implicite, même si `Option Strict` est activé.  
  
 Quand vous appelez une méthode avec un argument dont le type de données est différent de celui du paramètre correspondant, une conversion restrictive provoque une erreur de compilation si `Option Strict` est défini sur on. Vous pouvez éviter l’erreur au moment de la compilation à l’aide d’une conversion étendue ou d’une conversion explicite.  
  
 Les erreurs de conversion restrictive implicite sont supprimées au moment de la compilation pour les conversions des éléments d’une collection `For Each…Next` en variable de contrôle de boucle. Cela se produit même si `Option Strict` est activé. Pour plus d’informations, consultez la section « conversions restrictives » dans [for each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Erreurs de liaison tardive  
 Un objet est à liaison tardive quand il est assigné à une propriété ou à une méthode d’une variable déclarée comme étant de type `Object`. Pour plus d’informations, consultez [liaison précoce et tardive](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Erreurs de type d’objet implicite  
 Les erreurs de type d’objet implicite se produisent quand un type approprié ne peut pas être déduit pour une variable déclarée, de sorte qu’un type `Object` est déduit. Cela se produit principalement quand vous utilisez une instruction `Dim` pour déclarer une variable sans utiliser une clause `As` et que `Option Infer` a la valeur Off. Pour plus d’informations, consultez [instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) et [spécification du langage Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 Pour les paramètres de méthode, la clause `As` est facultative si `Option Strict` est désactivé. Toutefois, si un paramètre utilise une clause `As`, ils doivent tous l’utiliser. Si `Option Strict` est activé, la clause `As` est requise pour chaque définition de paramètre.  
  
 Si vous déclarez une variable sans utiliser de clause `As` et que vous la définissez sur `Nothing`, la variable a un type de `Object`. Aucune erreur de compilation ne se produit dans ce cas lorsque `Option Strict` est activé et que `Option Infer` est activé. `Dim something = Nothing`en est un exemple.  
  
### <a name="default-data-types-and-values"></a>Types de données et valeurs par défaut  
 Le tableau suivant décrit les résultats de différentes combinaisons de spécification du type de données et de l’initialiseur dans une [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|  
|---|---|---|---|  
|Non|Non|`Dim qty`|Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Non|Oui|`Dim qty = 5`|Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur. Consultez [inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données. Pour plus d’informations, consultez [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Quand une instruction option strict n’est pas présente  
 Si le code source ne contient pas d’instruction `Option Strict`, le paramètre **option strict** sur la [page compiler, concepteur de projets (Visual Basic),](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé. La **page de compilation** contient des paramètres qui offrent un contrôle supplémentaire sur les conditions qui génèrent une erreur.  
  
 Si vous utilisez le compilateur de ligne de commande, vous pouvez utiliser l’option [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) du compilateur pour spécifier un paramètre pour `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Pour définir option strict dans l’IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. Dans l’**Explorateur de solutions**, sélectionnez un projet. Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
2. Sous l’onglet **compiler** , définissez la valeur dans la zone **option strict** .  
  
### <a name="conditions"></a>Pour définir des configurations d’avertissement dans l’IDE  
 Lorsque vous utilisez la [page compiler du concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) au lieu d’une instruction `Option Strict`, vous avez un contrôle supplémentaire sur les conditions qui génèrent des erreurs. La section **configurations d’avertissement** de la **page compiler** contient des paramètres qui correspondent aux trois conditions qui provoquent une erreur au moment de la compilation lorsque `Option Strict` est activé. Voici ces paramètres :  
  
- **Conversion implicite**  
  
- **Liaison tardive ; l’appel peut échouer au moment de l’exécution**  
  
- **Type implicite ; objet pris par défaut**  
  
 Quand vous affectez la valeur **On** à **Option Strict**, chacun de ces trois paramètres de configuration d’avertissement prend la valeur **Erreur**. Quand vous affectez la valeur **Off** à **Option Strict**, chacun des trois paramètres prend la valeur **Aucun**.  
  
 Vous pouvez remplacer individuellement chaque paramètre de configuration d’avertissement par **Aucun**, **Avertissement** ou **Erreur**. Si les trois paramètres de configuration d’avertissement ont la valeur **Erreur**, `On` s’affiche dans la zone `Option strict`. Si les trois ont la valeur **Aucun**, `Off` apparaît dans cette zone. Pour toute autre combinaison de ces paramètres, **(personnalisé)** s’affiche.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Pour définir le paramètre option strict par défaut pour les nouveaux projets  
 Lorsque vous créez un projet, le paramètre **option strict** de l’onglet **compiler** est défini sur le paramètre **option strict** de la boîte de dialogue **options** .  
  
 Pour définir `Option Strict` dans cette boîte de dialogue, dans le menu **Outils** , cliquez sur **options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial dans les **valeurs par défaut VB** est `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Pour définir option strict sur la ligne de commande  
 Incluez l’option [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) du compilateur dans la commande **vbc** .  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent des erreurs de compilation provoquées par des conversions de types implicites qui sont des conversions restrictives. Cette catégorie d’erreurs correspond à la condition de **conversion implicite** sur la **page compiler**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une erreur de compilation provoquée par la liaison tardive. Cette catégorie d’erreurs correspond à la **liaison tardive ; l’appel peut échouer au moment** de l’exécution sur la **page compiler**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent des erreurs provoquées par des variables déclarées avec un type implicite de `Object`. Cette catégorie d’erreurs correspond au **type implicite ; condition supposée** par l’objet sur la **page de compilation**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Voir aussi

- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit (instruction)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Guide pratique : accéder aux membres d’un objet](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Liaison tardive dans les solutions Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
