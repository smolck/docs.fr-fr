---
title: 'Tutorial: Catégoriser les questions de soutien - classification multiclasse'
description: Découvrez comment utiliser ML.NET dans un scénario de classification multiclasse pour classer des problèmes GitHub et les affecter à une zone donnée.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: f158b8dce81e00f652496cad4ec9217c516b3e9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739712"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a>Tutorial: Catégoriser les problèmes de support à l’aide de la classification multiclasse avec ML.NET

Ce tutoriel montre comment utiliser ML.NET pour créer un classifieur de problèmes GitHub afin d’entraîner un modèle qui classe et prédit l’étiquette Area d’un problème GitHub par le biais d’une application console .NET Core en C# dans Visual Studio.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Préparer vos données
> * Transformer les données
> * Effectuer l’apprentissage du modèle
> * Évaluer le modèle
> * Prédire avec le modèle entraîné
> * Déployer et prédire avec un modèle chargé

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou plus tard ou Visual Studio 2017 version 15.6 ou plus tard avec le ".NET Core cross-platform development" charge de travail installée.
* Le [GitHub émet l’onglet séparé fichier (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* Le [GitHub émet l’onglet de test séparé fichier (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Création d’une application console

### <a name="create-a-project"></a>Création d’un projet

1. Ouvrez Visual Studio 2017. Sélectionnez **File** > **New** > **Project** à partir de la barre de menu. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**. Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez « GitHubIssueClassification », puis cliquez sur le bouton **OK**.

2. Créez un répertoire nommé *Données* dans votre projet pour enregistrer vos fichiers de jeu de données :

    Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « Données » et appuyez sur Entrée.

3. Créez un répertoire nommé *Models* dans votre projet pour enregistrer votre modèle :

    Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « Models » et appuyez sur Entrée.

4. Installez le **package NuGet Microsoft.ML** :

    Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**. Choisissez «nuget.org» comme source de paquet, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML** et sélectionnez le bouton **Installer.** Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

### <a name="prepare-your-data"></a>Préparer vos données

1. Téléchargez les jeux de données [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) et [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv), puis enregistrez-les dans le dossier *Données* créé précédemment. Le premier jeu de données effectue l’apprentissage automatique du modèle, et le second peut servir à évaluer la précision de votre modèle.

2. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur chacun des fichiers \*.tsv, puis sélectionnez **Propriétés**. Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* : 

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

Créez trois champs globaux pour accueillir les chemins des fichiers récemment téléchargés, puis des variables globales pour `MLContext`, `DataView` et `PredictionEngine` :

* `_trainDataPath` contient le chemin d’accès au jeu de données utilisé pour l’apprentissage du modèle.
* `_testDataPath` contient le chemin d’accès au jeu de données utilisé pour évaluer le modèle.
* `_modelPath` contient le chemin d’accès où le modèle formé est enregistré.
* `_mlContext` est le <xref:Microsoft.ML.MLContext> qui fournit le contexte de traitement.
* `_trainingDataView` est le <xref:Microsoft.ML.IDataView> utilisé pour traiter le jeu de données d’entraînement.
* `_predEngine` est le <xref:Microsoft.ML.PredictionEngine%602> utilisé pour des prédictions uniques.

Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins et les autres variables :

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

Créez des classes pour vos données d’entrée et vos prévisions. Ajoutez une nouvelle classe à votre projet :

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *GitHubIssueData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

    Le fichier *GitHubIssueData.cs* s’ouvre dans l’éditeur de code. Ajoutez l’instruction `using` suivante en haut de *GitHubIssueData.cs* :

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

Supprimez la définition de classe existante et ajoutez le code suivant, lequel contient deux classes (`GitHubIssue` et `IssuePrediction`), au fichier *GitHubIssueData.cs* :

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

`label` est la colonne à prédire. Les valeurs `Features` identifiées sont les entrées que vous fournissez au modèle pour prédire l’étiquette.

Utilisez [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) pour spécifier les index des colonnes sources dans le jeu de données.

`GitHubIssue`, la classe de jeu de données d’entrée, comprend les champs <xref:System.String> suivants :

* La première colonne `ID` est l’ID du problème GitHub.
* La deuxième colonne `Area` est la prédiction pour l’entraînement.
* La troisième colonne `Title` (titre du problème GitHub) est la première caractéristique (`feature`) utilisée pour prédire l’étiquette `Area`
* La quatrième colonne `Description` est la deuxième caractéristique (`feature`) utilisée pour prédire `Area`

`IssuePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé. Il a `string` un`Area`seul `PredictedLabel` `ColumnName` ( ) et un attribut.  L’attribut `PredictedLabel` est utilisé pendant la prédiction et l’évaluation. L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.

Toutes les opérations ML.NET commencent dans la classe [MLContext.](xref:Microsoft.ML.MLContext) L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle. Sur le plan conceptuel, cette classe est similaire à `DBContext` dans `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

Initialisez la variable globale `_mlContext` à l’aide d’une nouvelle instance de `MLContext` avec une valeur de départ aléatoire (`seed: 0`) pour obtenir des résultats reproductibles/déterministes dans différents entraînements.  Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Chargement des données

ML.NET utilise la [classe IDataView](xref:Microsoft.ML.IDataView) comme un moyen flexible et efficace de décrire des données tabulaires au format numérique ou texte. `IDataView` peut charger des fichiers texte ou en temps réel (par exemple, une base de données SQL ou des fichiers journaux).

Pour initialiser et charger la variable globale `_trainingDataView` afin de l’utiliser pour le pipeline, ajoutez le code suivant après l’initialisation de `mlContext` :

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier. Elle prend les variables de chemin de données et retourne un `IDataView`.

Ajoutez le code suivant comme prochaine ligne dans la méthode `Main` :

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

La méthode `ProcessData` exécute les tâches suivantes :

* Extrait et transforme les données.
* Retourne le pipeline de traitement.

Créez la méthode `ProcessData` juste après la méthode `Main`, en utilisant le code suivant :

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Extraire des caractéristiques et transformer les données

Pour prédire l’étiquette Area GitHub pour un `GitHubIssue`, utilisez la méthode [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) afin de transformer la colonne `Area` en une colonne `Label` de type clé numérique (un format accepté par les algorithmes de classification) et ajoutez-la comme nouvelle colonne au jeu de données :

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

Ensuite, `mlContext.Transforms.Text.FeaturizeText`appelez , qui transforme`Title` `Description`le texte ( et ) `TitleFeaturized` `DescriptionFeaturized`colonnes en un vecteur numérique pour chacun appelé et . Utilisez le code suivant pour ajouter la caractérisation des deux colonnes au pipeline :

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

La dernière étape de préparation des données consiste à combiner toutes les colonnes de caractéristiques dans la colonne **Features** à l’aide de la méthode [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A). Par défaut, un algorithme d’apprentissage traite uniquement les caractéristiques issues de la colonne **Features**. Utilisez le code suivant pour ajouter cette transformation au pipeline :

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 Ajoutez ensuite un <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> pour mettre en cache le DataView. Ainsi, quand vous itérerez plusieurs fois sur les données, l’utilisation du cache vous fera peut-être gagner en performances, à l’instar du code suivant :

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> Utilisez AppendCacheCheckpoint pour les jeux de données petits/moyens afin de réduire le temps d’apprentissage. Ne l’utilisez PAS (supprimez .AppendCacheCheckpoint()) lors du traitement de jeux de données très volumineux.

Retournez le pipeline à la fin de la méthode `ProcessData`.

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

Cette étape gère le prétraitement/la caractérisation. L’utilisation des composants supplémentaires disponibles dans ML.NET peut améliorer les résultats de votre modèle.

## <a name="build-and-train-the-model"></a>Générer et entraîner le modèle

Ajoutez l’appel suivant à la méthode `BuildAndTrainModel` comme prochaine ligne de code dans la méthode `Main` :

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

La méthode `BuildAndTrainModel` exécute les tâches suivantes :

* Crée la classe d’algorithme d’entraînement.
* Effectue l’apprentissage du modèle.
* Prédit la zone en fonction des données d’entraînement.
* Retourne le modèle.

Créez la méthode `BuildAndTrainModel` juste après la méthode `Main`, en utilisant le code suivant :

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>À propos de la tâche de classification

La classification est une tâche de machine learning qui utilise des données pour **déterminer** la catégorie, le type ou la classe d’un élément ou d’une ligne de données. Cette tâche est souvent d’un de ces types :

* Binaire : A ou B.
* Multiclasse : plusieurs catégories pouvant être prédites à l’aide d’un modèle unique.

Pour ce type de problème, utilisez un algorithme de machine learning de classification multiclasse, dans la mesure où votre prédiction de catégorie de problème peut appartenir à une catégorie parmi plusieurs possibles (multiclasse) plutôt qu’à une catégorie parmi deux possibles (binaire).

Ajoutez l’algorithme de machine learning aux définitions de transformation de données en ajoutant la première ligne de code suivante dans `BuildAndTrainModel()` :

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) est l’algorithme de machine learning de classification multiclasse. Il est ajouté à `pipeline` et accepte les caractéristiques `Title` et `Description` (`Features`) ainsi que les paramètres d’entrée `Label` pour apprendre à partir des données d’historique.

### <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

Ajustez le modèle aux données `splitTrainSet` et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `BuildAndTrainModel()` :

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

La méthode `Fit()` entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API utile qui vous permet de passer et d’exécuter une prédiction sur une seule instance de données. Ajoutez ce contenu à la ligne suivante dans la méthode `BuildAndTrainModel()` :

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Prédire avec le modèle entraîné

Ajoutez un problème GitHub pour tester la prédiction du modèle entraîné dans la méthode `Predict` en créant une instance de `GitHubIssue` :

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

Utilisez la fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) pour effectuer une prédiction sur une seule ligne de données :

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Utilisation des résultats du modèle : prédiction

Affichez `GitHubIssue` et la prédiction d’étiquette `Area` correspondante pour partager les résultats et prendre les mesures nécessaires.  Créez une vue des résultats à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Retourner le modèle entraîné à utiliser pour l’évaluation

Retournez le modèle à la fin de la méthode `BuildAndTrainModel`.

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Évaluer le modèle

Maintenant que vous avez créé et effectué l’apprentissage du modèle, vous devez l’évaluer avec un jeu de données différent à des fins d’assurance qualité et de validation. Dans la méthode `Evaluate`, le modèle créé dans `BuildAndTrainModel` est passé pour évaluation. Créez la méthode `Evaluate` juste après `BuildAndTrainModel`, comme dans le code suivant :

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

La méthode `Evaluate` exécute les tâches suivantes :

* Charge le jeu de données de test.
* Crée l’évaluateur multiclasse.
* Évalue le modèle et crée des métriques.
* Affiche les métriques.

Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `BuildAndTrainModel`, en utilisant le code suivant :

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

Comme vous l’avez fait précédemment avec le jeu de données d’entraînement, chargez le jeu de données de test en ajoutant le code suivant à la méthode `Evaluate` :

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

La méthode [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) calcule les métriques de qualité pour le modèle à l’aide du jeu de données spécifié. Elle retourne un objet <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> contenant les métriques globales calculées par les évaluateurs de classification multiclasse.
Pour afficher les métriques permettant de déterminer la qualité du modèle, vous devez d’abord les obtenir.
Notez l’utilisation de la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) de la variable globale de machine learning `_trainedModel` (un [ITransformer](xref:Microsoft.ML.ITransformer)) pour entrer les caractéristiques et retourner les prédictions. Ajoutez comme nouvelle ligne le code suivant à la méthode `Evaluate` :

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

Les métriques suivantes sont évaluées pour la classification multiclasse :

* Micro-précision : chaque paire exemple-classe contribue de manière égale à la métrique de précision.  Vous voulez que Micro Accuracy soit aussi proche que possible.

* Macro-précision : chaque classe contribue de manière égale à la métrique de précision. Les classes minoritaires sont aussi importantes que les classes plus grandes. Vous voulez que Macro Accuracy soit aussi proche que possible d’un.

* Perte logarithmique : consultez [Perte logarithmique](../resources/glossary.md#log-loss). Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.

* Réduction des pertes de journal - Varie de [-inf, 1,00], où 1,00 est des prédictions parfaites et 0 indique des prédictions moyennes. Vous voulez que la réduction des pertes de connexion soit aussi proche que possible.

### <a name="displaying-the-metrics-for-model-validation"></a>Affichage des métriques pour la validation du modèle

Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Enregistrer le modèle dans un fichier

Une fois que vous êtes satisfait de votre modèle, enregistrez-le dans un fichier pour faire des prédictions ultérieurement ou dans une autre application. Ajoutez le code suivant à la méthode `Evaluate` .

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

Créez la méthode `SaveModelAsFile` sous votre méthode `Evaluate`.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Ajoutez le code suivant à votre méthode `SaveModelAsFile`. Ce code [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) utilise la méthode pour sérialiser et stocker le modèle formé comme un fichier zip.

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Déployer et prédire avec un modèle

Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `Evaluate`, en utilisant le code suivant :

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

Créez la méthode `PredictIssue`, juste après la méthode `Evaluate` (et juste avant la méthode `SaveModelAsFile`), en utilisant le code suivant :

```csharp
private static void PredictIssue()
{

}
```

La méthode `PredictIssue` exécute les tâches suivantes :

* Charge le modèle enregistré.
* Crée un problème unique de données de test.
* Prédit Area en fonction des données de test.
* Combine les données de test et les prédictions pour générer des rapports.
* Affiche les résultats prédits.

Chargez le modèle enregistré dans votre application en ajoutant le code suivant à la méthode `PredictIssue` :

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

Ajoutez un problème GitHub pour tester la prédiction du modèle entraîné dans la méthode `Predict` en créant une instance de `GitHubIssue` :

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

Comme vous l’avez fait précédemment, créez une instance `PredictionEngine` avec le code suivant :

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la `PredictionEnginePool` sécurité des fils [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans les environnements de production, utilisez le service, qui crée un des objets à utiliser dans toute votre application. Voir ce guide sur la façon [d’utiliser `PredictionEnginePool` dans un ASP.NET’API Web de base](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> L’extension de service `PredictionEnginePool` est disponible en préversion.

Utilisez `PredictionEngine` pour prédire l’étiquette Area GitHub en ajoutant le code suivant à la méthode `PredictIssue` servant à la prédiction :

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Utilisation du modèle chargé pour la prédiction

Affichez `Area` pour catégoriser le problème et agir en conséquence. Créez une vue des résultats à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a>Résultats

Vos résultats doivent être similaires à ce qui suit. Lors du traitement, le pipeline affiche des messages. Vous pouvez voir des avertissements ou des messages de traitement. Ces messages ont été supprimés des résultats suivants par souci de clarté.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Félicitations ! Vous venez de créer un modèle d’apprentissage automatique pour la classification et la prédiction d’une étiquette Area d’un problème GitHub. Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Préparer vos données
> * Transformer les données
> * Effectuer l’apprentissage du modèle
> * Évaluer le modèle
> * Prédire avec le modèle entraîné
> * Déployer et prédire avec un modèle chargé

Passer au tutoriel suivant pour en savoir plus
> [!div class="nextstepaction"]
> [Prédiction du prix d’une course de taxi](predict-prices.md)
