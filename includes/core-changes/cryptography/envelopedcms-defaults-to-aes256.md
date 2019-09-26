---
ms.openlocfilehash: b965c3a975b0f2cadd906799fef1665261d96d6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181974"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="56182-101">La valeur par défaut de EnvelopedCms est le chiffrement AES-256</span><span class="sxs-lookup"><span data-stu-id="56182-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="56182-102">L’algorithme de chiffrement symétrique `EnvelopedCms` par défaut utilisé par est passé de TripleDES à AES-256.</span><span class="sxs-lookup"><span data-stu-id="56182-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="details"></a><span data-ttu-id="56182-103">Détails</span><span class="sxs-lookup"><span data-stu-id="56182-103">Details</span></span>

<span data-ttu-id="56182-104">Dans .net Core Preview 7 et les versions antérieures, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> quand est utilisé pour chiffrer des données sans spécifier un algorithme de chiffrement symétrique via une surcharge de constructeur, les données ont été chiffrées avec l’algorithme TripleDES/3DES/3DEA/des3-EDE.</span><span class="sxs-lookup"><span data-stu-id="56182-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="56182-105">À compter de .NET Core 3,0 Preview 8 (via la version 4.6.0 du package NuGet [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ), l’algorithme par défaut a été remplacé par AES-256 pour la modernisation des algorithmes et pour améliorer la sécurité des options par défaut.</span><span class="sxs-lookup"><span data-stu-id="56182-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="56182-106">Si un certificat de destinataire de message a une clé publique Diffie-Hellman non-EC, l’opération de chiffrement peut échouer avec un <xref:System.Security.Cryptography.CryptographicException> en raison des limitations de la plateforme sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="56182-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="56182-107">Dans l’exemple de code suivant, les données sont chiffrées à l’aide de TripleDES si vous exécutez .NET Core 3,0 Preview 7 ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="56182-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="56182-108">En cas d’exécution sur .NET Core 3,0 Preview 8 ou version ultérieure, il est chiffré avec AES-256.</span><span class="sxs-lookup"><span data-stu-id="56182-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="56182-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="56182-109">Version introduced</span></span>

<span data-ttu-id="56182-110">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="56182-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56182-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="56182-111">Recommended action</span></span>

<span data-ttu-id="56182-112">Si vous avez un impact négatif sur la modification, vous pouvez restaurer le chiffrement TripleDes en spécifiant explicitement l’identificateur d’algorithme <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> de chiffrement dans un constructeur qui <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>comprend un paramètre de type, par exemple :</span><span class="sxs-lookup"><span data-stu-id="56182-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="56182-113">Category</span><span class="sxs-lookup"><span data-stu-id="56182-113">Category</span></span>

<span data-ttu-id="56182-114">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="56182-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56182-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="56182-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->