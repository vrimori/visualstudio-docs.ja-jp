---
title: サポートされていないデータベース プロバイダーのデータベース オブジェクトが選択されています
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5b6eef41ebd3ae6fc08029a618cf276e22001235
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116880"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>サポートされていないデータベース プロバイダーのデータベース オブジェクトが選択されています

**O/R デザイナー** for SQL Server、.NET Framework Data Provider のみをサポートしています (<xref:System.Data.SqlClient>)。 クリックすることができますが**OK**とサポートされていないデータベース プロバイダーからオブジェクトを使用して、実行時に予期しない動作が発生する可能性があります。

> [!NOTE]
> .NET Framework Data Provider for SQL Server を使用するデータ接続のみがサポートされます。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- **[OK]** をクリックします。

   サポートされていないデータベース プロバイダーを使用する接続にマップされるエンティティ クラスのデザインを続行できます。 サポートされないデータベース プロバイダーを使用すると、予期しない動作が発生することがあります。

    - または -

- クリックして**キャンセル**します。

   操作が停止されます。 .NET Framework Provider for SQL Server を使用するデータ接続を作成または使用してください。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)