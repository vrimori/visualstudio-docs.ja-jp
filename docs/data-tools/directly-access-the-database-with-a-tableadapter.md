---
title: "方法 : TableAdapter で直接データベースにアクセスする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "データベース [Visual Basic], アクセス (TableAdapter による)"
  - "データセット [Visual Basic], 追加 (プロジェクトに)"
  - "DBDirect メソッド"
  - "GenerateDbDirectMethods プロパティ"
  - "保存 (データを)"
  - "TableAdapter.Delete メソッド"
  - "TableAdapter.GenerateDBDirectMethods プロパティ"
  - "TableAdapter.Insert メソッド"
  - "TableAdapter.Update メソッド"
  - "TableAdapter"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : TableAdapter で直接データベースにアクセスする
`InsertCommand`、`UpdateCommand`、および `DeleteCommand` 以外に、データベースに対して直接実行できるメソッドも、TableAdapter に設定できます。  これらのメソッド \(`TableAdapter.Insert`、`TableAdapter.Update`、および `TableAdapter.Delete`\) は、データベース内でデータを直接操作するために呼び出すことができます。  
  
 これらの直接メソッドを作成しない場合は、**\[プロパティ\]** ウィンドウで TableAdapter の `GenerateDbDirectMethods` プロパティを `false` に設定します。  メイン クエリに加えて TableAdapter に追加されたクエリは、スタンドアロンのクエリです。つまり、DbDirect メソッドを生成しないクエリです。  
  
## データベースへのコマンドの直接送信  
 目的とするタスクを実行する TableAdapter DbDirect メソッドを呼び出します。  
  
#### 新規レコードをデータベースに直接挿入するには  
  
-   各列の値をパラメーターとして渡して TableAdapter の `Insert` メソッドを呼び出します。  次の手順では、例として Northwind データベースの `Region` テーブルを使用します。  
  
    > [!NOTE]
    >  使用できるインスタンスがない場合は、使用する TableAdapter をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### データベース内のレコードを直接更新するには  
  
-   各列の新しい値と元の値をパラメーターとして渡して TableAdapter の `Update` メソッドを呼び出します。  
  
    > [!NOTE]
    >  使用できるインスタンスがない場合は、使用する TableAdapter をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### データベース内のレコードを直接削除するには  
  
-   各列の値を `Delete` メソッドのパラメーターとして渡して TableAdapter の `Delete` メソッドを呼び出します。  この例では、Northwind データベースの `Region` テーブルを使用します。  
  
    > [!NOTE]
    >  使用できるインスタンスがない場合は、使用する TableAdapter をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## 参照  
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [コマンドとパラメーター](../Topic/Commands%20and%20Parameters.md)