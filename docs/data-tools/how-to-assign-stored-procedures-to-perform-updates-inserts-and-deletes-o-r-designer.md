---
title: "How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes (O/R Designer)
ストアド プロシージャは O\/R デザイナーに追加でき、通常の <xref:System.Data.Linq.DataContext> メソッドとして実行できます。これらを使用して、エンティティ クラスからデータベースに変更が保存されたときに \(たとえば、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> メソッドを呼び出したときに\) 挿入、更新、および削除を実行する既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムの動作をオーバーライドすることもできます。  
  
> [!NOTE]
>  ストアド プロシージャが、クライアントに送信する必要のある値 \(たとえば、ストアド プロシージャで計算された値\) を返す場合は、ストアド プロシージャに出力パラメーターを作成します。出力パラメーターを使用できない場合は、O\/R デザイナーによって生成されたオーバーライドを利用するのではなく、部分メソッドを実装します。データベースによって生成される値にマップされるメンバーは、INSERT 操作または UPDATE 操作が正常に完了した後で、適切な値に設定する必要があります。詳細については、「[Responsibilities of the Developer In Overriding Default Behavior](../Topic/Responsibilities%20of%20the%20Developer%20In%20Overriding%20Default%20Behavior.md)」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] は、ID 列 \(自動インクリメント\)、rowguidcol 列 \(データベースが生成した GUID\)、およびタイムスタンプ列であれば、データベースによって生成された値を自動的に処理します。その他の列型のデータベースが生成した値は、予想に反して null 値になります。データベースが生成した値を返すには、手動で <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> を `true` に設定し、<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> を <xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync>、または <xref:System.Data.Linq.Mapping.AutoSync> のいずれかに設定する必要があります。  
  
## エンティティ クラスの更新動作の構成  
 既定では、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] エンティティ クラスのデータに対して行われた変更でデータベースを更新 \(挿入、更新、および削除\) するロジックは、[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムによって提供されます。ランタイムは、テーブルのスキーマ \(列および主キー情報\) に基づいて、既定の Insert、Update、および Delete の各コマンドを作成します。既定の動作を使用しない場合は、テーブルのデータの操作に必要な Insert、Update、および Delete を実行する特定のストアド プロシージャを割り当てることで、更新動作を構成できます。この方法は、既定の動作が生成されていない場合、たとえばエンティティ クラスがビューにマップされている場合にも実行できます。最後に、データベースのテーブルへのアクセスには常にストアド プロシージャを通すようにすると、既定の更新動作をオーバーライドできます。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### ストアド プロシージャを割り当てて、エンティティ クラスの既定の動作をオーバーライドするには  
  
1.  デザイナーで **LINQ to SQL** ファイルを開きます \(**ソリューション エクスプローラー**で .dbml ファイルをダブルクリックします\)。  
  
2.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、**\[ストアド プロシージャ\]** を展開し、エンティティ クラスの Insert、Update、Delete の各コマンドで使用するストアド プロシージャを探します。  
  
3.  ストアド プロシージャを O\/R デザイナーにドラッグします。  
  
     ストアド プロシージャが <xref:System.Data.Linq.DataContext> メソッドとしてメソッド ペインに追加されます。詳細については、「[DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)」を参照してください。  
  
4.  更新の実行にストアド プロシージャを使用するエンティティ クラスを選択します。  
  
5.  **\[プロパティ\]** ウィンドウで、オーバーライドするコマンド \(**\[Insert\]**、**\[Update\]**、または **\[Delete\]**\) を選択します。  
  
6.  **\[ランタイムを使用\]** の横にある省略記号 \(\[...\]\) をクリックして、**\[動作の構成\]** ダイアログ ボックスを開きます。  
  
7.  **\[カスタマイズ\]** を選択します。  
  
8.  **\[カスタマイズ\]** の一覧で、目的のストアド プロシージャをクリックします。  
  
9. **\[メソッドの引数\]** および **\[クラスのプロパティ\]** の一覧を調べて、**\[メソッドの引数\]** が適切な **\[クラスのプロパティ\]** にマップされていることを確認します。Update コマンドと Delete コマンドについて、元のメソッド引数 \(Original\_*ArgumentName*\) を元のプロパティ \(*PropertyName* \(オリジナル\)\) にマップします。  
  
    > [!NOTE]
    >  既定では、メソッド引数は名前が一致した場合にクラス プロパティにマップされます。変更されたプロパティ名がテーブルとエンティティ クラス間で一致しなくなり、デザイナーが正しいマッピングを判断できないときは、マップ先となる同等のクラス プロパティを選択することが必要になる場合があります。  
  
10. **\[OK\]** または **\[適用\]** をクリックします。  
  
    > [!NOTE]
    >  変更を行うたびに **\[適用\]** をクリックすると、各クラスと動作の組み合わせに対して動作の構成を続行できます。**\[適用\]** をクリックする前にクラスまたは動作を変更した場合は、警告ダイアログ ボックスが表示され、ここで変更を適用できます。  
  
     更新時に既定のランタイム ロジックを使用するように戻すには、**\[プロパティ\]** ウィンドウで、\[Insert\]、\[Update\]、または \[Delete\] の各コマンドの横にある省略記号をクリックし、**\[動作の構成\]** ダイアログ ボックスで **\[ランタイムを使用\]** を選択します。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [チュートリアル: Northwind の Customers テーブル用 Update ストアド プロシージャの作成](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Insert, Update, and Delete Operations](../Topic/Insert,%20Update,%20and%20Delete%20Operations.md)