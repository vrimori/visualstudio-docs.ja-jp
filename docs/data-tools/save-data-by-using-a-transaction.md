---
title: '方法: トランザクションを使用してデータを保存'
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f4c865dcf55f8796748308822b8a6dde5f96ef8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920548"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>方法: トランザクションを使用してデータを保存
使用して、トランザクションでデータを保存する、<xref:System.Transactions>名前空間。 使用して、<xref:System.Transactions.TransactionScope>を自動的に管理されているトランザクションに参加するオブジェクト。

トランザクションを使用するプロジェクトへの参照を手動で追加する必要があるために、System.Transactions アセンブリへの参照ではプロジェクトは作成されません。

トランザクションを実装する最も簡単な方法がインスタンスを作成するには、<xref:System.Transactions.TransactionScope>内のオブジェクト、`using`ステートメントです。 (詳細については、次を参照してください[Using ステートメント](/dotnet/visual-basic/language-reference/statements/using-statement)、および[ステートメントを使用して](/dotnet/csharp/language-reference/keywords/using-statement)。)。内で実行されるコード、`using`ステートメントが、トランザクションに参加します。

トランザクションをコミットするには、呼び出し、<xref:System.Transactions.TransactionScope.Complete%2A>メソッドを使用して、最後のステートメントとしてをブロックします。

トランザクションをロールバックしてを呼び出す前に例外をスロー、<xref:System.Transactions.TransactionScope.Complete%2A>メソッドです。

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>System.Transactions.dll への参照を追加するには

1.  **プロジェクト**メニューの **参照の追加**です。

2.  **.NET**  タブ (**SQL Server**プロジェクトの SQL Server タブ) を選択**System.Transactions**、し、 **OK**です。

     System.Transactions.dll への参照がプロジェクトに追加されます。

## <a name="to-save-data-in-a-transaction"></a>トランザクションでデータを保存するには

-   使用して、内のデータを保存するコードを追加トランザクションを含むステートメント。 次のコードを作成およびインスタンス化する方法を示しています、<xref:System.Transactions.TransactionScope>オブジェクトを使用して、ステートメント。

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)
- [チュートリアル: トランザクションにデータを保存する](../data-tools/save-data-in-a-transaction.md)