---
title: "選択した接続がサポートされないデータベース プロバイダーを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: abd7ba49b3a9bb449f4f323deee588c3942d37a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選択した接続では、サポートされていないデータベース プロバイダーが使用されています
SQL Server からの .NET Framework データ プロバイダーを使用しない項目をドラッグすると、このメッセージが表示される**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [LINQ to SQLVisual Studio tools](../data-tools/linq-to-sql-tools-in-visual-studio2.md)です。  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]では、.NET Framework Provider for SQL Server を使用するデータ接続のみがサポートされます。 有効な接続は、Microsoft SQL Server または Microsoft SQL Server データベース ファイルへの接続だけです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   .NET Framework Data Provider for SQL Server を使用するデータ接続の項目のみを [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加します。  
  
## <a name="see-also"></a>関連項目
<xref:System.Data.SqlClient>  
[O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)  
[Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
