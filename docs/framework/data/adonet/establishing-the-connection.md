---
title: Établissement de la connexion
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 4606ecb370b7e85cf5ebd92754471f5253321251
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149659"
---
# <a name="establishing-the-connection"></a>Établissement de la connexion
Pour vous connecter à Microsoft SQL Server, utilisez l'objet <xref:System.Data.SqlClient.SqlConnection> du fournisseur de données .NET Framework pour SQL Server. Pour vous connecter à une source de données OLE DB, utilisez l'objet <xref:System.Data.OleDb.OleDbConnection> du fournisseur de données .NET Framework pour OLE DB. Pour vous connecter à une source de données ODBC, utilisez l'objet <xref:System.Data.Odbc.OdbcConnection> du fournisseur de données .NET Framework pour ODBC. Pour vous connecter à une source de données Oracle, utilisez l'objet <xref:System.Data.OracleClient.OracleConnection> du fournisseur de données .NET Framework pour Oracle. Pour stocker et récupérer en toute sécurité les chaînes de connexion, voir [Protecting Connection Information](protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Fermeture de connexions  
 Nous vous recommandons de toujours fermer la connexion lorsque vous avez fini de l'utiliser, de façon à ce qu'elle puisse être retournée au pool. Le bloc `Using` dans Visual Basic ou C# supprime automatiquement la connexion lorsque le code quitte le bloc, même dans le cas d'une exception non traitée. Voir [l’utilisation de l’énoncé](../../../csharp/language-reference/keywords/using-statement.md) et [l’utilisation de l’énoncé](../../../visual-basic/language-reference/statements/using-statement.md) pour plus d’informations.  
  
 Vous pouvez également utiliser la méthode `Close` ou `Dispose` de l'objet de connexion pour le fournisseur que vous utilisez. Les connexions qui ne sont pas explicitement fermées risquent de ne pas être ajoutées ni retournées au pool. Par exemple, une connexion devenue hors de portée mais qui n'a pas été explicitement fermée sera retournée au pool de connexion seulement si la taille maximale de celui-ci a été atteinte et si la connexion est toujours valide. Pour plus d’informations, voir [OLE DB, ODBC et Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
> N’appelez `Close` `Dispose` pas ou sur une **connexion,** un **DataReader**, ou tout autre objet géré dans la `Finalize` méthode de votre classe. Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement. Si votre classe ne possède pas de ressource non managée, n'incluez pas une méthode `Finalize` dans la définition de classe. Pour plus d’informations, voir [Collection des ordures](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Les événements de connexion et de déconnexion ne seront pas déclenchés sur le serveur si une connexion est récupérée depuis le pool de connexions ou qu’elle est retournée au pool, car elle n’est pas réellement fermée lorsqu’elle est retournée au pool. Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Connexion à SQL Server  
 Le fournisseur de données .NET Framework pour SQL Server prend en charge un format de chaîne de connexion similaire à celui de la chaîne de connexion OLE DB (ADO). Pour obtenir les noms et les valeurs de format de chaîne valides, voir la propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection>. Vous pouvez également utiliser la classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion valides du point de vue de la syntaxe au moment de l'exécution. Pour plus d’informations, consultez [Builders de chaînes de connexion](connection-string-builders.md).  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une base de données SQL Server.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a>Sécurité intégrée et ASP.NET  
 La sécurité intégrée SQL Server (également appelée « connexions approuvées ») fournit une protection lors de la connexion à SQL Server car elle n'expose pas d'ID utilisateur et de mot de passe dans la chaîne de connexion, et elle est la méthode recommandée pour l'authentification d'une connexion. La sécurité intégrée utilise l'identité de sécurité active, ou jeton, du processus en cours d'exécution. Dans les applications bureautiques, il s'agit généralement de l'identité de l'utilisateur actuellement connecté.  
  
 Dans les applications ASP.NET, l'identité de sécurité peut être définie à l'aide d'une option parmi plusieurs options différentes. Pour mieux comprendre l’identité de sécurité qu’une application ASP.NET utilise lors de la connexion à SQL Server, voir [ASP.NET’usurpation d’identité](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentification](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), et [comment: Accéder au serveur SQL en utilisant windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Connexion à une source de données OLE DB  
 Le fournisseur de données cadre .NET pour OLE DB fournit une connectivité aux sources de données exposées à l’aide d’OLE DB (par l’intermédiaire de SQLOLEDB, le fournisseur OLE DB pour SQL Server), à l’aide de l’objet **OleDbConnection.**  
  
 Pour le fournisseur de données .NET Framework pour OLE DB, le format de chaîne de connexion est identique à celui utilisé dans ADO, avec les exceptions suivantes :  
  
- Le mot clé **fournisseur** est requis.  
  
- Les mots clés **URL,** **Remote Provider**et **Remote Server** ne sont pas pris en charge.  
  
 Pour plus d'informations sur les chaînes de connexion OLE DB, voir la rubrique <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>. Vous pouvez également utiliser <xref:System.Data.OleDb.OleDbConnectionStringBuilder> pour créer des chaînes de connexion au moment de l'exécution.  
  
> [!NOTE]
> L’objet **OleDbConnection** ne prend pas en charge le réglage ou la récupération de propriétés dynamiques spécifiques à un fournisseur OLE DB. Seules les propriétés pouvant être passées dans la chaîne de connexion du fournisseur OLE DB sont prises en charge.  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données OLE DB.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a>N'utilisez pas de fichiers UDL (Universal Data Link)  
 Il est possible de fournir des informations de connexion pour un **OleDbConnection** dans un fichier Universal Data Link (UDL); cependant, vous devriez éviter de le faire. Les fichiers UDL n'étant pas chiffrés, ils exposent les informations de chaîne de connexion en texte brut. Comme un fichier UDL est une ressource basée sur un fichier externe pour votre application, il n'est pas possible de le sécuriser à l'aide du .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Connexion à une source de données ODBC  
 Le fournisseur de données cadre .NET pour ODBC fournit une connectivité aux sources de données exposées à l’aide d’ODBC à l’aide de l’objet **OdbcConnection.**  
  
 Pour le fournisseur de données .NET Framework pour ODBC, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion ODBC. Vous pouvez également fournir un nom de source de données ODBC (DSN). Pour plus de détails sur **l’OdbcConnection** , voir le <xref:System.Data.Odbc.OdbcConnection>.  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données ODBC.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a>Connexion à une source de données Oracle  
 Le fournisseur de données cadre .NET pour Oracle fournit une connectivité aux sources de données Oracle à l’aide de l’objet **OracleConnection.**  
  
 Pour le fournisseur de données .NET Framework pour Oracle, le format de la chaîne de connexion est conçu pour être aussi proche que possible du format de la chaîne de connexion du fournisseur de données OLE DB pour Oracle (MSDAORA). Pour plus de détails sur l’OracleConnection , voir le **OracleConnection** <xref:System.Data.OracleClient.OracleConnection>.  
  
 L'exemple de code suivant illustre la création et l'ouverture d'une connexion à une source de données Oracle.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a>Voir aussi

- [Connexion à une source de données](connecting-to-a-data-source.md)
- [Cordes de connexion](connection-strings.md)
- [Regroupement de connexions OLE DB, ODBC et Oracle](ole-db-odbc-and-oracle-connection-pooling.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
