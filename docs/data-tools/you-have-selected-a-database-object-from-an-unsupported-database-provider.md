---
title: "You have selected a database object from an unsupported database provider | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# You have selected a database object from an unsupported database provider
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) では、.NET Framework Data Provider for SQL Server \(<xref:System.Data.SqlClient>\) のみがサポートされます。**\[OK\]** をクリックし、サポートされないデータベース プロバイダーからオブジェクトの処理を続行することもできますが、実行時に予期しない動作が発生することがあります。  
  
> [!NOTE]
>  .NET Framework Data Provider for SQL Server を使用するデータ接続のみがサポートされます。  
  
### このエラーを解決するには  
  
-   **\[OK\]** をクリックして、サポートされないデータベース プロバイダーを使用する接続にマップされるエンティティ クラスのデザインを続行します。サポートされないデータベース プロバイダーを使用すると、予期しない動作が発生することがあります。  
  
     または  
  
-   **\[キャンセル\]** をクリックします。  
  
     操作が停止されます。.NET Framework Provider for SQL Server を使用するデータ接続を作成または使用してください。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [.NET Framework データ プロバイダー](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)