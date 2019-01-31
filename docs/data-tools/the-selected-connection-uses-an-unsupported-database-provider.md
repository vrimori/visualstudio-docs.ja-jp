---
title: 選択した接続では、サポートされていないデータベース プロバイダーが使用されています
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c59716342a26607842adca1e896177de2eb3facc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000186"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選択した接続では、サポートされていないデータベース プロバイダーが使用されています

.NET Framework Data Provider for SQL Server を使用しない項目をドラッグすると、このメッセージが表示されます**サーバー エクスプ ローラー**または**データベース エクスプ ローラー**上に、[ビジュアルでの LINQ to SQL ツールStudio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)します。

**O/R デザイナー** for SQL Server、.NET Framework Provider を使用するデータ接続のみをサポートします。 有効な接続は、Microsoft SQL Server または Microsoft SQL Server データベース ファイルへの接続だけです。

このエラーを修正するには、SQL server、.NET Framework Data Provider を使用するデータ接続から項目のみを追加、 **O/R デザイナー**します。

## <a name="see-also"></a>関連項目

- <xref:System.Data.SqlClient>
- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
