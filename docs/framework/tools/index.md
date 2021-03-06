---
title: Outils du .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 60a9cb241f289cacc7437174f112114e843aca47
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645564"
---
# <a name="net-framework-tools"></a>Outils du .NET Framework

Les outils du .NET Framework facilitent la création, le déploiement et la gestion d'applications et de composants qui ciblent le .NET Framework.

La plupart des outils .NET Framework décrits dans cette section sont installés automatiquement avec Visual Studio. Pour télécharger Visual Studio, visitez la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).

Vous pouvez exécuter tous les outils de la ligne de commande à l’exception de l’Assembly Cache Viewer (*Shfusion.dll*). Vous devez accéder à *Shfusion.dll* de File Explorer.
  
Le meilleur moyen d'exécuter l'outil en ligne de commande consiste à utiliser l'invite de commandes développeur Visual Studio. Ces utilitaires vous permettent d’exécuter facilement les outils, sans naviguer jusqu’au dossier d’installation. Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

> [!NOTE]
> Certains outils sont spécifiques aux ordinateurs 32 bits ou aux ordinateurs 64 bits. Veillez à exécuter la version appropriée de l'outil pour votre ordinateur.

## <a name="in-this-section"></a>Contenu de cette section

- [Al.exe (Assembly Linker)](al-exe-assembly-linker.md)  
Génère un fichier qui possède un manifeste de l'assembly issu de modules ou de fichiers de ressources.

- [Aximp.exe (Windows Forms ActiveX Control Importer)](aximp-exe-windows-forms-activex-control-importer.md)  
Convertit les définitions de types d'une bibliothèque de types COM d'un contrôle ActiveX en contrôle Windows Forms.

- [Caspol.exe (Code Access Security Policy Tool)](caspol-exe-code-access-security-policy-tool.md)  
Permet d'afficher et de configurer la stratégie de sécurité au niveau de l'ordinateur, de l'utilisateur et de l'entreprise. Dans le cadre .NET 4 et plus tard, cet outil n’affecte pas la politique de sécurité `true`d’accès au code (CAS) à moins que [ \<l’héritageCasPolicy> élément](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) est fixé à . Pour plus d’informations, consultez [Changements en matière de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

- [Cert2spc.exe (Software Publisher Certificate Test Tool)](cert2spc-exe-software-publisher-certificate-test-tool.md)  
Crée un certificat SPC (Software Publisher's Certificate) à partir d'un ou plusieurs certificats X.509. Cet outil ne doit être utilisé qu'à des fins de test.

- [Certmgr.exe (Certificate Manager Tool)](certmgr-exe-certificate-manager-tool.md)  
Gère les certificats, les listes de certificats de confiance (CTL) et les listes de révocation de certificats (CRL).

- [Clrver.exe (outil de version CLR)](clrver-exe-clr-version-tool.md)  
Signale toutes les versions installées de l’heure d’exécution de langue commune (CLR) sur l’ordinateur.

- [Invite de commande](developer-command-prompt-for-vs.md)  
Vous permet d’utiliser plus facilement les outils cadres .NET. Il s’agit d’une invite de commandes qui définit automatiquement les variables d’environnement spécifiques.

- [CorFlags.exe (Outil de conversion CorFlags)](corflags-exe-corflags-conversion-tool.md)  
Vous permet de configurer la section CorFlags de l'en-tête d'une image exécutable portable (PE).

- [Fuslogvw.exe (Assembly Binding Log Viewer)](fuslogvw-exe-assembly-binding-log-viewer.md)  
Affiche des informations sur les liaisons d'assembly pour vous aider à diagnostiquer ce qui empêche le .NET Framework de trouver l'assembly au moment de l'exécution.

- [Gacutil.exe (Global Assembly Cache Tool)](gacutil-exe-gac-tool.md)  
Vous permet de visualiser et de manipuler le contenu du Global Assembly Cache et du cache de téléchargement.

- [Ilasm.exe (IL Assembler)](ilasm-exe-il-assembler.md)  
Génère un fichier PE (exécutable portable) en langage IL (Intermediate Language). Vous pouvez exécuter le fichier exécutable obtenu pour déterminer si le langage IL fonctionne comme prévu.

- [Ildasm.exe (il Démonteur)](ildasm-exe-il-disassembler.md)  
Utilise un fichier PE qui contient le code IL (Intermediate Language) et crée un fichier texte qu'il peut utiliser en entrée dans l'Assembleur IL (Ilasm.exe).

- [Installutil.exe (Outil d’installation)](installutil-exe-installer-tool.md)  
Permet d'installer et de désinstaller des ressources serveur en exécutant les composants d'installation d'un assembly spécifié. (Utilise les classes dans l'espace de noms <xref:System.Configuration.Install>.)

- [Lc.exe (Compilateur de licence)](lc-exe-license-compiler.md)  
Lit les fichiers texte qui contiennent des informations de licence et produit un fichier *.licenses* qui peut être intégré dans une langue commune runtime exécutable comme une ressource.

- [Mage.exe (Manifeste Génération et outil d’édition)](mage-exe-manifest-generation-and-editing-tool.md)  
Permet de créer, de modifier et de signer des manifestes d'application et de déploiement. En tant qu’outil en ligne de commande, *Mage.exe* peut être exécuté à partir de scripts de commandes par lot et d’autres applications Windows, notamment les applications ASP.NET.

- [MageUI.exe (Manifeste Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
Prend en charge les mêmes fonctionnalités que l'outil en ligne de commande Mage.exe, mais utilise une interface utilisateur de type Windows. Prend en charge les mêmes fonctionnalités que l’outil de ligne de commande *Mage.exe*, mais utilise une interface utilisateur (UI) basée sur Windows.

- [MDbg.exe (.NET Framework Command-Line Debugger)](mdbg-exe.md)  
Permet aux fournisseurs d'outils et aux développeurs d'applications de trouver et de corriger les bogues dans les programmes qui ont pour cible le Common Language Runtime du .NET Framework. Cet outil utilise l'API de débogage du runtime pour fournir des services de débogage.

- [Mgmtclassgen.exe (Gestion Fortement Typé Générateur de classe)](mgmtclassgen-exe.md)  
Permet de générer une classe managée à liaison anticipée pour une classe Windows Management Instrumentation spécifiée (WMI).

- [Mpgo.exe (Outil d’optimisation guidée de profil géré)](mpgo-exe-managed-profile-guided-optimization-tool.md)  
Vous permet d'ajuster les assemblys d'image native en utilisant des scénarios courants d'utilisateurs finaux. Mpgo.exe permet la génération et la consommation des données de profil pour les assemblys d’application d’image native (pas les assemblys .NET Framework) à l’aide de scénarios de formation sélectionnés par le développeur d’applications.

- [Ngen.exe (Générateur d’images indigènes)](ngen-exe-native-image-generator.md)  
Améliore les performances des applications managées via l'utilisation d'images natives (fichiers qui contiennent le code machine spécifique au processeur compilé). Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.

- [Peverify.exe (PEVerify Tool)](peverify-exe-peverify-tool.md)  
Permet de vérifier si votre code MSIL (Microsoft Intermediate Language) et les métadonnées associées satisfont aux exigences de cohérence des types.

- [Regasm.exe (Outil d’enregistrement de l’Assemblée)](regasm-exe-assembly-registration-tool.md)  
Lit les métadonnées dans un assembly et ajoute les entrées nécessaires au Registre. Cela permet aux clients COM d'apparaître en tant que classes .NET Framework.

- [Regsvcs.exe (.NET Services Installation Tool)](regsvcs-exe-net-services-installation-tool.md)  
Charge et enregistre un assembly, génère et installe une bibliothèque de types dans une application COM+ version 1.0 spécifiée et configure les services que vous avez ajoutés par programmation à une classe.

- [Resgen.exe (Générateur de fichiers de ressources)](resgen-exe-resource-file-generator.md)  
Convertit les fichiers texte (*.txt* ou *.restext)* et les fichiers de format de ressources xML *(.resx)* en fichiers binaires *(.ressources)* courants qui peuvent être intégrés dans un runtime binaire exécutable ou compilé dans des assemblages satellites.

- [SecAnnotate.exe (.NET Security Annotator Tool)](secannotate-exe-net-security-annotator-tool.md)  
Identifie les parties `SecurityCritical` et `SecuritySafeCritical` d'un assembly.

- [SignTool.exe (Outil de signe)](signtool-exe.md)  
Signe numériquement les fichiers, vérifie les signatures dans les fichiers et insère un horodatage dans les fichiers.

- [Sn.exe (Outil de nom fort)](sn-exe-strong-name-tool.md)  
Facilite la création d'assemblys avec des noms forts. Cet outil fournit des options de gestion des clés, de génération des signatures et de vérification des signatures.

- [SOS.dll (EXTENSION DE débâage SOS)](sos-dll-sos-debugging-extension.md)  
Vous aide à déboguer des programmes managés dans le débogueur WinDbg.exe et dans Visual Studio en fournissant des informations sur l'environnement interne du CLR (Common Language Runtime).

- [SqlMetal.exe (Code Generation Tool)](sqlmetal-exe-code-generation-tool.md)  
Génère le code et le mappage pour le composant LINQ to SQL du .NET Framework.

- [Storeadm.exe (Outil de stockage isolé)](storeadm-exe-isolated-storage-tool.md)  
Gère le stockage isolé en proposant des options pour répertorier les magasins de l'utilisateur et les supprimer.

- [Tlbexp.exe (Type Library Exporter)](tlbexp-exe-type-library-exporter.md)  
Génère une bibliothèque de types décrivant les types définis dans un assembly du Common Language Runtime.

- [Tlbimp.exe (Importateur de bibliothèque de type)](tlbimp-exe-type-library-importer.md)  
Convertit les définitions de types présentes dans une bibliothèque de types COM en définitions équivalentes dans un assembly de Common Language Runtime.

- [Winmdexp.exe (Windows Runtime Metadata Export Tool)](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
Exporte un assemblage cadre .NET qui est compilé comme un fichier *.winmdobj* dans un composant Windows Runtime, qui est emballé comme un fichier *.winmd* qui contient à la fois des métadonnées Windows Runtime et des informations de implémentation.

- [Winres.exe (Windows Forms Resource Editor)](winres-exe-windows-forms-resource-editor.md)  
Vous aide à localiser les ressources d’interface utilisateur (interface utilisateur)*(fichiers .resx* ou *.resources)* qui sont utilisées par Windows Forms. Vous pouvez traduire des chaînes puis dimensionner, déplacer et masquer les contrôles comme vous le souhaitez afin de placer les chaînes localisées.

## <a name="related-sections"></a>Sections connexes

- [outils WPF](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))  
Inclut des outils comme l’outil isXPS Conformance (isXPS.exe) et les outils de profilage des performances.

- [Outils de Windows Communication Foundation](../wcf/tools.md)  
Inclut des outils qui facilitent la création, le déploiement et la gestion d'applications Windows Communication Foundation (WCF).
