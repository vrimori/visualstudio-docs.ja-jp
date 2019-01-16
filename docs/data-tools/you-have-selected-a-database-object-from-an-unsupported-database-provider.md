---
title: サポートされていないデータベース プロバイダーのデータベース オブジェクトが選択されています
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4efaf92c9f4688d6870c1152be27eb4c8f4ed933
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894442"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>サポートされていないデータベース プロバイダーのデータベース オブジェクトが選択されています

**O/R デザイナー** for SQL Server、.NET Framework Data Provider のみをサポートしています (<xref:System.Data.SqlClient>)。 **[OK]** をクリックし、サポートされないデータベース プロバイダーからオブジェクトの処理を続けることもできますが、実行時に予期しない動作が発生することがあります。

> [!NOTE]
> .NET Framework Data Provider for SQL Server を使用するデータ接続のみがサポートされます。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- **[OK]** をクリックします。

   サポートされていないデータベース プロバイダーを使用する接続にマップされるエンティティ クラスのデザインを続行できます。 サポートされないデータベース プロバイダーを使用すると、予期しない動作が発生することがあります。

    - または -

- **[キャンセル]** をクリックします。

   操作が停止されます。 .NET Framework Provider for SQL Server を使用するデータ接続を作成または使用してください。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)