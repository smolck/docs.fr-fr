---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291641"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure : packages d’intégration Azure préfixés par Microsoft supprimés

Les `Microsoft.*` packages suivants qui assurent l’intégration entre les ASP.net Core et les kits de développement logiciel (SDK) Azure ne sont pas inclus dans ASP.NET Core 5,0 :

* [Microsoft. extensions. Configuration. AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), qui intègre [Azure Key Vault](/azure/key-vault/) dans le [système de configuration](/aspnet/core/fundamentals/configuration/).
* [Microsoft. AspNetCore. dataprotection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), qui intègre Azure Key Vault dans le [système de Protection des données ASP.net Core](/aspnet/core/security/data-protection/introduction).
* [Microsoft. AspNetCore. dataprotection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), qui intègre le [stockage d’objets BLOB Azure](/azure/storage/blobs/) dans le système de protection des données ASP.net core.

Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 1

#### <a name="old-behavior"></a>Ancien comportement

Les `Microsoft.*` packages intègrent les services Azure avec les API de configuration et de protection des données.

#### <a name="new-behavior"></a>Nouveau comportement

`Azure.*`Les nouveaux packages intègrent les services Azure avec les API de configuration et de protection des données.

#### <a name="reason-for-change"></a>Motif de modification

La modification a été apportée parce que les `Microsoft.*` packages étaient :

* À l’aide de versions obsolètes du kit de développement logiciel (SDK) Azure. Les mises à jour simples n’étaient pas possibles car les nouvelles versions du kit de développement logiciel (SDK) Azure comprenaient des modifications avec rupture.
* Lié au calendrier des versions de .NET Core. Le transfert de la propriété des packages à l’équipe du kit de développement logiciel (SDK) Azure active les mises à jour du package lors de la mise à jour du kit SDK Azure.

#### <a name="recommended-action"></a>Action recommandée

Dans ASP.NET Core projets 2,1 ou versions ultérieures, remplacez l’ancien `Microsoft.*` par les nouveaux `Azure.*` packages.

| Ancien | Nouveau |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure. AspNetCore. DataProtection. Keys](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure. AspNetCore. DataProtection. blob](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure. extensions. Configuration. secrets](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

Les nouveaux packages utilisent une nouvelle version du kit de développement logiciel (SDK) Azure qui comprend des modifications avec rupture. Les modèles d’utilisation générale sont inchangés. Certaines surcharges et options peuvent varier pour s’adapter aux modifications apportées aux API du kit de développement logiciel (SDK) Azure sous-jacentes.

Les anciens packages vont :

* Être pris en charge par l’équipe ASP.NET Core pendant la durée de vie de .NET Core 2,1 et 3,1.
* Ne sont pas inclus dans .NET 5.

Lors de la mise à niveau de votre projet vers .NET 5, effectuez la transition vers les `Azure.*` packages pour maintenir la prise en charge.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
