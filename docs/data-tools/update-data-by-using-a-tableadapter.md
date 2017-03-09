---
title: "方法 : TableAdapter を使用してデータを更新する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "データ [Visual Studio], TableAdapter"
  - "データ [Visual Studio], 更新"
  - "保存 (データを)"
  - "TableAdapter, 更新 (データを)"
  - "更新 (データを), TableAdapter"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : TableAdapter を使用してデータを更新する
データセット内のデータを変更して検証したら、更新されたデータをデータベースに戻す必要があります。  変更したデータをデータベースに送信するには、[TableAdapter](../data-tools/tableadapter-overview.md) の `Update` メソッドを呼び出します。  アダプターの `Update` メソッドによって単一のデータ テーブルが更新され、正しいコマンド \(INSERT、UPDATE、または DELETE\) がテーブル内の各データ行の <xref:System.Data.DataRow.RowState%2A> に基づいて実行されます。  関連するテーブルのデータを保存する場合は、Visual Studio によって TableAdapterManager コンポーネントが作成されます。このコンポーネントは、データベースで定義された外部キー制約に基づく適切な順序で保存を実行するときに役立ちます。  詳細については、「[階層更新の概要](../Topic/Hierarchical%20Update%20Overview.md)」を参照してください。  
  
> [!NOTE]
>  データセットの内容でデータ ソースを更新しようとするとエラーが発生する場合があるため、アダプターの `Update` メソッドを呼び出すコードは `try`\/`catch` ブロック内に配置する必要があります。  
  
 データ ソースを更新する実際の手順はビジネス ニーズによって異なる場合がありますが、アプリケーションでは次の手順に従う必要があります。  
  
1.  `try`\/`catch` ブロック内にあるアダプターの `Update` メソッドを呼び出します。  
  
2.  例外が検出された場合は、エラーを引き起こしたデータ行を探します。  詳細については、「[方法 : エラーが発生している行を探す](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md)」を参照してください。  
  
3.  データ行の問題を調整し \(可能な場合はプログラムで調整し、可能でない場合は修正のためにユーザーに無効な行を表示する\)、もう一度更新してみます \(<xref:System.Data.DataRow.HasErrors%2A>、<xref:System.Data.DataTable.GetErrors%2A>\)。  
  
## データベースへのデータの保存  
 TableAdapter の `Update` メソッドを呼び出し、データベースに書き込まれる値を含むデータ テーブルの名前を渡します。  
  
#### TableAdapter を使用して、データセットが存在するデータベースを更新するには  
  
-   `Update` メソッドを `try`\/`catch` ブロックで囲みます。  `try`\/`catch` ブロック内で `NorthwindDataSet` の `Customers` テーブルの内容を更新する方法の例を次に示します。  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## TableAdapter によるデータセット内の 2 つの関連テーブルの更新  
 データセットの関連テーブルを更新する場合は、適切な順序で更新し、参照整合性の制約に違反する可能性を小さくする必要があります。  コマンド実行の順序も、データセットの <xref:System.Data.DataRowCollection> のインデックスに従います。  データの整合性エラーが発生しないようにするには、最も適切な方法として、次の順序でデータベースを更新します。  
  
1.  子テーブル : レコードを削除する。  
  
2.  親テーブル : レコードを挿入、更新、および削除する。  
  
3.  子テーブル : レコードを挿入および更新する。  
  
    > [!NOTE]
    >  複数の関連テーブルを更新する場合、トランザクション内にすべての更新ロジックを含める必要があります。  トランザクションは、変更をコミットする前に、関連するすべての変更を正しくデータベースに反映できることを確認するプロセスです。  詳細については、「[トランザクションと同時実行](../Topic/Transactions%20and%20Concurrency.md)」を参照してください。  
  
#### TableAdapter を使用した 2 つの関連するテーブルの更新  
  
1.  3 つの一時データ テーブルを作成して異なるレコードを格納します。  
  
2.  `try`\/`catch` ブロックから、それぞれの行サブセットに対する `Update` メソッドを呼び出します。  更新エラーが起きた場合は、エラーを分岐して解決する必要があります。  
  
3.  データベースに変更内容をコミットします。  
  
4.  一時データ テーブルを破棄し、リソースを解放します。  
  
     関連テーブルを含むデータセットによってデータ ソースを更新する方法を次の例に示します。  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_2.cs)]  
  
## 参照  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)