---
title: "How to: Create an Association (Relationship) Between LINQ to SQL Classes (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Create an Association (Relationship) Between LINQ to SQL Classes (O/R Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] のエンティティ クラス間の関連付けは、データベース内のテーブル間の関連付けに似ています。**\[関連付けエディター\]** ダイアログ ボックスを使用することで、エンティティ クラス間の関連付けを作成できます。  
  
 **\[関連付けエディター\]** ダイアログ ボックスを使用して関連付けを作成するときは、親クラスと子クラスを選択する必要があります。親クラスは、主キーを含むエンティティ クラスであり、子クラスは、外部キーを含むエンティティ クラスです。たとえば、Northwind の Customers テーブルと Orders テーブルにマップされるエンティティ クラスが作成された場合は、Customer クラスが親クラスであり、Order クラスが子クラスです。  
  
> [!NOTE]
>  **サーバー エクスプローラー**または**データベース エクスプローラー**から[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) にテーブルをドラッグすると、データベース内の既存の外部キー リレーションシップに基づいて関連付けが自動的に作成されます。  
  
 関連付けの作成後、O\/R デザイナーで関連付けを選択すると、**\[プロパティ\]** ウィンドウにいくつかの構成可能なプロパティが表示されます。関連付けは、関連クラス間の線で表されます。次の表は、関連付けのプロパティの説明を示しています。  
  
|プロパティ|説明|  
|-----------|--------|  
|**カーディナリティ**|関連付けが 1 対多と 1 対 1 のどちらであるかを制御します。|  
|**子プロパティ**|コレクションのプロパティを親に作成するか、子レコードへの参照を関連付けの外部キー側に作成するかを指定します。たとえば、Customer と Order 間の関連付けでは、**"子プロパティ"** が **True** に設定され、Orders という名前のプロパティが親クラスに作成されます。|  
|**親プロパティ**|関連付けられている親クラスを参照する子クラスのプロパティです。たとえば、Customer と Order の間の関連付けでは、注文に関連付けられている顧客を参照する Customer という名前のプロパティが Order クラスに作成されます。|  
|**関与のプロパティ**|関連付けのプロパティを表示し、**\[関連付けエディター\]** ダイアログ ボックスを再び開く**省略記号**ボタン \(...\) が用意されています。|  
|**ユニーク**|外部ターゲット列に一意性の制約があるかどうかを示します。|  
  
### エンティティ クラス間に関連付けを作成するには  
  
1.  関連付けの親クラスを表すエンティティ クラスを右クリックし、**\[追加\]** をポイントして、**\[関連付け\]** をクリックします。  
  
2.  **\[関連付けエディター\]** ダイアログ ボックスで、正しい**親クラス**が選択されていることを確認します。  
  
3.  コンボ ボックスで**子クラス**を選択します。  
  
4.  クラスに関連する **\[関連付けのプロパティ\]** を選択します。通常、これはデータベースで定義されている外部キー リレーションシップにマップされます。たとえば、Customers と Orders の関連付けでは、**\[関連付けのプロパティ\]** は各クラスの CustomerID になります。  
  
5.  **\[OK\]** をクリックして、関連付けを作成します。  
  
## 参照  
 [O\/R Designer Overview](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [How to: Represent Primary Keys](../Topic/How%20to:%20Represent%20Primary%20Keys.md)