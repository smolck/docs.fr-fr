---
title: -main (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 7d3cfce474023907eda0bc40b692e4bbb65ffb96
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802842"
---
# <a name="-main-c-compiler-options"></a>-main (Options du compilateur C#)
Cette option spécifie la classe qui contient le point d’entrée du programme dans le cas où plusieurs classes contiennent une méthode **Main**.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 Type contenant la méthode **Main**.  
 Le nom de classe fourni doit être complet, c’est-à-dire qu’il doit inclure l’espace de noms complet contenant la classe, suivi du nom de classe. Par exemple, si la méthode `Main` se trouve dans la classe `Program` dans l’espace de noms `MyApplication.Core`, l’option du compilateur doit être `-main:MyApplication.Core.Program`.
  
## <a name="remarks"></a>Notes  
 Si votre compilation comprend plusieurs types avec une méthode [Main](../../programming-guide/main-and-command-args/index.md), vous pouvez spécifier le type qui contient la méthode **Main** à utiliser comme point d’entrée dans le programme.  
  
 Cette option est à utiliser lors de la compilation d’un fichier .exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet.  
  
2. Cliquez sur la page de propriétés **Application**.  
  
3. Modifiez la propriété **Objet de démarrage**.  
  
     Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a>Pour définir cette option du compilateur en modifiant manuellement le fichier. csproj
  
Vous pouvez définir cette option en modifiant le fichier. csproj et en ajoutant un élément `StartupObject` à l’intérieur de la `PropertyGroup` section. Par exemple :

```
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a>Exemple  
 Compilez `t2.cs` et `t3.cs`, en spécifiant que la **Main** se trouve dans `Test2` :  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
