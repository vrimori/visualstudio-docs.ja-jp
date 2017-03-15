---
title: "方法 : トランザクションを使用してデータを保存する | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 保存"
  - "保存 (データを), 使用 (トランザクションを)"
  - "System.Transactions 名前空間"
  - "トランザクション, 保存 (データを)"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : トランザクションを使用してデータを保存する
トランザクションでは、<xref:System.Transactions> 名前空間を使用してデータを保存します。  <xref:System.Transactions.TransactionScope> オブジェクトを使用して、自動的に管理されるトランザクションに参加します。  
  
 プロジェクトに対する System.Transactions アセンブリへの参照は作成されないので、トランザクションを使用するプロジェクトへの参照は手動で追加する必要があります。  
  
> [!NOTE]
>  <xref:System.Transactions> 名前空間は、Windows 2000 以降でサポートされます。  
  
 トランザクションを実装する最も簡単な方法は、`using` ステートメントで <xref:System.Transactions.TransactionScope> オブジェクトをインスタンス化することです。  詳細については、「[Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)」と「[using ステートメント](/dotnet/csharp/language-reference/keywords/using-statement)」を参照してください。`using` ステートメント内で実行されるコードは、トランザクションに参加します。  
  
 トランザクションをコミットするには、using ブロックの最後のステートメントとして <xref:System.Transactions.TransactionScope.Complete%2A> メソッドを呼び出します。  
  
 トランザクションをロールバックするには、<xref:System.Transactions.TransactionScope.Complete%2A> メソッドを呼び出す前に例外をスローします。  
  
 詳細については、「[チュートリアル : トランザクションのデータの保存](../data-tools/save-data-in-a-transaction.md)」を参照してください。  
  
### System.Transactions の DLL への参照を追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[参照の追加\]** を選択します。  
  
2.  **\[.NET\]** タブで **System.Transactions** を選択し \(SQL Server プロジェクトでは **\[SQL Server\]** タブ\)、**\[OK\]** をクリックします。  
  
     System.Transactions.dll への参照がプロジェクトに追加されます。  
  
### トランザクションのデータを保存するには  
  
-   トランザクションを含む using ステートメントにデータを保存するコードを追加します。  using ステートメントで <xref:System.Transactions.TransactionScope> オブジェクトを作成してインスタンス化する方法のコード例を次に示します。  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## 参照  
 [チュートリアル : トランザクションのデータの保存](../data-tools/save-data-in-a-transaction.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)