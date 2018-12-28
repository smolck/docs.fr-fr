---
title: Charger des données à partir de plusieurs fichiers pour le traitement machine learning - ML.NET
description: Découvrez comment charger des données à partir de plusieurs fichiers pour les utiliser lors de la création, l’entraînement et le scoring de modèles Machine Learning avec ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c9b34bd6bcbac62e9f9c33226f5d0feb41168392
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150730"
---
# <a name="load-data-from-multiple-files-for-machine-learning-processing---mlnet"></a><span data-ttu-id="a6ae2-103">Charger des données à partir de plusieurs fichiers pour le traitement machine learning - ML.NET</span><span class="sxs-lookup"><span data-stu-id="a6ae2-103">Load data from multiple files for machine learning processing - ML.NET</span></span>

<span data-ttu-id="a6ae2-104">Utilisez `TextLoader` et spécifiez un tableau de fichiers à la méthode `Read`.</span><span class="sxs-lookup"><span data-stu-id="a6ae2-104">Use the `TextLoader`, and specify an array of files to the `Read` method.</span></span> <span data-ttu-id="a6ae2-105">Les fichiers doivent avoir le même schéma (même nombre et type de colonnes) :</span><span class="sxs-lookup"><span data-stu-id="a6ae2-105">The files must have the same schema (same number and type of columns):</span></span>

* [<span data-ttu-id="a6ae2-106">Exemple de fichier1</span><span class="sxs-lookup"><span data-stu-id="a6ae2-106">Example file1</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.train)
* [<span data-ttu-id="a6ae2-107">Exemple de fichier2</span><span class="sxs-lookup"><span data-stu-id="a6ae2-107">Example file2</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.test)

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // A boolean column depicting the 'label'.
        new TextLoader.Column("IsOver50k", DataKind.BL, 0),
        // Three text columns.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
        new TextLoader.Column("Education", DataKind.TX, 2),
        new TextLoader.Column("MaritalStatus", DataKind.TX, 3)
    },
    // First line of the file is a header, not a data row.
    HasHeader = true
});

var data = reader.Read(exampleFile1, exampleFile2);
```