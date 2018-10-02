---
title: データベース オブジェクトでサポートされていないデータベース プロバイダーを選択した |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c225e00a6d303bff16e30fabd2f3e8e0e9d40ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547271"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>サポートされていないデータベース プロバイダーのデータベース オブジェクトが選択されています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 2017 ドキュメント](https://docs.microsoft.com/en-us/visualstudio/)します。  
  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) For SQL Server、.NET Framework Data Provider のみをサポートしています (<xref:System.Data.SqlClient>)。 クリックすることができますが**OK**とサポートされていないデータベース プロバイダーからオブジェクトを使用して、実行時に予期しない動作が発生する可能性があります。  
  
> [!NOTE]
>  .NET Framework Data Provider for SQL Server を使用するデータ接続のみがサポートされます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   クリックして**OK**サポートされていないデータベース プロバイダーを使用する接続にマップされるエンティティ クラスのデザインを続行します。 サポートされないデータベース プロバイダーを使用すると、予期しない動作が発生することがあります。  
  
     - または -  
  
-   クリックして**キャンセル**します。  
  
     操作が停止されます。 .NET Framework Provider for SQL Server を使用するデータ接続を作成または使用してください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [.NET framework データ プロバイダー](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)

