---
title: Contrôle d'accès
description: Découvrez comment contrôler l’accès aux éléments de programmation, tels que les types, les méthodes et les fonctions F# , dans le langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425108"
---
# <a name="access-control"></a>Contrôle d'accès

*Le contrôle d’accès* fait référence à la déclaration des clients qui peuvent utiliser certains éléments de programme, tels que des types, des méthodes et des fonctions.

## <a name="basics-of-access-control"></a>Notions de base de Access Control

Dans F#, les spécificateurs de contrôle d’accès `public`, `internal`et `private` peuvent être appliqués à des modules, des types, des méthodes, des définitions de valeur, des fonctions, des propriétés et des champs explicites.

- `public` indique que l’entité est accessible par tous les appelants.

- `internal` indique que l’entité est accessible uniquement à partir du même assembly.

- `private` indique que l’entité est accessible uniquement à partir du type englobant ou du module.

> [!NOTE]
> Le spécificateur d’accès `protected` n’est pas utilisé F#dans, bien qu’il soit acceptable si vous utilisez des types créés dans des langages qui prennent en charge l’accès `protected`. Par conséquent, si vous substituez une méthode protégée, votre méthode reste accessible uniquement dans la classe et ses descendants.

En général, le spécificateur est placé devant le nom de l’entité, sauf lorsqu’un spécificateur `mutable` ou `inline` est utilisé, qui apparaît après le spécificateur de contrôle d’accès.

Si aucun spécificateur d’accès n’est utilisé, la valeur par défaut est `public`, à l’exception des liaisons `let` dans un type, qui sont toujours `private` au type.

Les signatures F# dans fournissent un autre mécanisme de contrôle F# de l’accès aux éléments de programme. Les signatures ne sont pas requises pour le contrôle d’accès. Pour plus d’informations, consultez [Signatures](signature-files.md).

## <a name="rules-for-access-control"></a>Règles pour Access Control

Le contrôle d’accès est soumis aux règles suivantes :

- Les déclarations d’héritage (autrement dit, l’utilisation de `inherit` pour spécifier une classe de base pour une classe), les déclarations d’interface (c’est-à-dire spécifier qu’une classe implémente une interface) et les membres abstraits ont toujours la même accessibilité que le type englobant. Par conséquent, un spécificateur de contrôle d’accès ne peut pas être utilisé sur ces constructions.

- L’accessibilité des cas individuels dans une union discriminée est déterminée par l’accessibilité de l’union discriminée elle-même. Autrement dit, un cas d’Union particulier n’est pas moins accessible que l’Union elle-même.

- L’accessibilité des champs individuels d’un type d’enregistrement est déterminée par l’accessibilité de l’enregistrement lui-même. Autrement dit, une étiquette d’enregistrement particulière n’est pas moins accessible que l’enregistrement lui-même.

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de spécificateurs de contrôle d’accès. Il y a deux fichiers dans le projet, `Module1.fs` et `Module2.fs`. Chaque fichier est implicitement un module. Par conséquent, il existe deux modules, `Module1` et `Module2`. Un type privé et un type interne sont définis dans `Module1`. Le type privé n’est pas accessible à partir de `Module2`, mais le type interne peut.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Le code suivant teste l’accessibilité des types créés dans `Module1.fs`.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F#](index.md)
- [Signatures](signature-files.md)
