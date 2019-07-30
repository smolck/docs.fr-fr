---
ms.openlocfilehash: df13f6938ebaf8e96bb2825c1495044621f1c31b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802630"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="1bc6a-101">ASP.NET ValidationContext.MemberName n’est pas NULL lors de l’utilisation d’un DataAnnotations.ValidationAttribute personnalisé</span><span class="sxs-lookup"><span data-stu-id="1bc6a-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1bc6a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="1bc6a-102">Details</span></span>|<span data-ttu-id="1bc6a-103">Dans .NET Framework 4.7.2 et versions antérieures, quand vous utilisez un <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personnalisé, la propriété <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retourne <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="1bc6a-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns <code>null</code>.</span></span>  <span data-ttu-id="1bc6a-104">Dans .NET Framework 4.8, elle retourne le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="1bc6a-104">In .NET Framework 4.8, it returns the member name.</span></span>|
|<span data-ttu-id="1bc6a-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="1bc6a-105">Suggestion</span></span>|<span data-ttu-id="1bc6a-106">Le comportement par défaut de la propriété <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> reste le même.</span><span class="sxs-lookup"><span data-stu-id="1bc6a-106">The default behavior of the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property remains the same.</span></span>  <span data-ttu-id="1bc6a-107">Pour récupérer une valeur valide à partir de la propriété <code>ValidationContext.MemberName</code>, ajoutez le paramètre suivant à votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="1bc6a-107">To retrieve a valid value from the <code>ValidationContext.MemberName</code> property, add the following setting to your app config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="1bc6a-108">Portée</span><span class="sxs-lookup"><span data-stu-id="1bc6a-108">Scope</span></span>|<span data-ttu-id="1bc6a-109">Inconnu</span><span class="sxs-lookup"><span data-stu-id="1bc6a-109">Unknown</span></span>|
|<span data-ttu-id="1bc6a-110">Version</span><span class="sxs-lookup"><span data-stu-id="1bc6a-110">Version</span></span>|<span data-ttu-id="1bc6a-111">4.8</span><span class="sxs-lookup"><span data-stu-id="1bc6a-111">4.8</span></span>|
|<span data-ttu-id="1bc6a-112">Type</span><span class="sxs-lookup"><span data-stu-id="1bc6a-112">Type</span></span>|<span data-ttu-id="1bc6a-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="1bc6a-113">Runtime</span></span>|
|<span data-ttu-id="1bc6a-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="1bc6a-114">Affected APIs</span></span>|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
