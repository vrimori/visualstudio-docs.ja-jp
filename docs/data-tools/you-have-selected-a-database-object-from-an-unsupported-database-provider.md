---
title: "サポートされていないデータベース プロバイダーからのデータベース オブジェクトを選択した |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 05e638be5cc11f66052e5a1f6116e7205b824106
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>サポートされていないデータベース プロバイダーのデータベース オブジェクトが選択されています
O/R デザイナーは、SQL Server の .NET Framework Data Provider のみをサポートしています (<xref:System.Data.SqlClient>)。 クリックしたり、 **OK**とサポートされないデータベース プロバイダーからオブジェクトの処理は引き続き、実行時に予期しない動作が発生する可能性があります。  
  
> [!NOTE]
>  .NET Framework Data Provider for SQL Server を使用するデータ接続のみがサポートされます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- **[OK]** をクリックします。

   サポートされていないデータベース プロバイダーを使用する接続にマップされるエンティティ クラスのデザインを続行することができます。 サポートされないデータベース プロバイダーを使用すると、予期しない動作が発生することがあります。  
  
     または  
  
- をクリックして**キャンセル**です。

   操作が停止されます。 .NET Framework Provider for SQL Server を使用するデータ接続を作成または使用してください。  
  
## <a name="see-also"></a>関連項目
[O/R デザイナー メッセージ](../data-tools/o-r-designer-messages.md)  
[Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)