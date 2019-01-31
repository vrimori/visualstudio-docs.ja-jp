---
title: '方法: トランザクションを使用してデータを保存する'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ecf63cc03af13cadb5791e2f0f5a058feedb8418
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934076"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>方法: トランザクションを使用してデータを保存する

使用して、トランザクションでデータを保存する、<xref:System.Transactions>名前空間。 使用して、<xref:System.Transactions.TransactionScope>オブジェクトが自動的に管理されているトランザクションに参加します。

参照を含むプロジェクトは作成されません、 *System.Transactions*アセンブリ、手動でトランザクションを使用するプロジェクトへの参照を追加する必要があるようにします。

トランザクションを実装する最も簡単な方法がインスタンス化するには、<xref:System.Transactions.TransactionScope>オブジェクト、`using`ステートメント。 (詳細については、次を参照してください[ステートメントを使用して](/dotnet/visual-basic/language-reference/statements/using-statement)、および[ステートメントを使用して](/dotnet/csharp/language-reference/keywords/using-statement)。)。内で実行されるコード、`using`ステートメントがトランザクションに参加します。

トランザクションをコミットするには、呼び出し、<xref:System.Transactions.TransactionScope.Complete%2A>メソッドを使用して、最後のステートメントをブロックします。

トランザクションをロールバックするには、呼び出す前に例外をスロー、<xref:System.Transactions.TransactionScope.Complete%2A>メソッド。

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System.Transactions.dll への参照を追加するには

1.  **プロジェクト**メニューの **参照の追加**します。

2.  **.NET**  タブ (**SQL Server**の SQL Server プロジェクト タブ) を選択します**System.Transactions**、し、 **OK**。

     参照を*System.Transactions.dll*プロジェクトに追加されます。

## <a name="to-save-data-in-a-transaction"></a>トランザクションでデータを保存するには

-   使用して、データを保存するコードを追加するが、トランザクションを含むステートメント。 次のコードを作成し、インスタンス化する方法を示しています、<xref:System.Transactions.TransactionScope>オブジェクトを使用して、ステートメント。

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)
- [チュートリアル: トランザクションにデータを保存する](../data-tools/save-data-in-a-transaction.md)