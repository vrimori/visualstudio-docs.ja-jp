---
title: サポートされていないデータベース プロバイダーからのデータベース オブジェクトを選択した |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5dfb475cdb1b63e4dfcaaebcda4b5d2dc3a7f070
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>サポートされていないデータベース プロバイダーのデータベース オブジェクトが選択されています
O/R デザイナーは、SQL Server の .NET Framework Data Provider のみをサポートしています (<xref:System.Data.SqlClient>)。 クリックしたり、 **OK**とサポートされないデータベース プロバイダーからオブジェクトの処理は引き続き、実行時に予期しない動作が発生する可能性があります。  
  
> [!NOTE]
>  .NET Framework Data Provider for SQL Server を使用するデータ接続のみがサポートされます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- **[OK]**をクリックします。

   サポートされていないデータベース プロバイダーを使用する接続にマップされるエンティティ クラスのデザインを続行することができます。 サポートされないデータベース プロバイダーを使用すると、予期しない動作が発生することがあります。  
  
     - または -  
  
- をクリックして**キャンセル**です。

   操作が停止されます。 .NET Framework Provider for SQL Server を使用するデータ接続を作成または使用してください。  
  
## <a name="see-also"></a>関連項目
[O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)  
[Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)