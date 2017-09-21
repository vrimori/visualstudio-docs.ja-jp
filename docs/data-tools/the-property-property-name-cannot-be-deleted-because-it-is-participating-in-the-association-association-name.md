---
title: "The property &lt;property name&gt; cannot be deleted because it is participating in the association &lt;association name&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The property &lt;property name&gt; cannot be deleted because it is participating in the association &lt;association name&gt;
選択されたプロパティは、エラー メッセージに示されているクラス間の関連付けに対する**関連付けプロパティ**として設定されています。プロパティがデータ クラス間の関連付けに関与している場合、そのプロパティを削除することはできません。  
  
 **関連付けプロパティ**をデータ クラスの別のプロパティに設定して、目的のプロパティが正常に削除されるようにしてください。  
  
### このエラーを解決するには  
  
1.  O\/R デザイナーで、エラー メッセージに示されているデータ クラスを接続する関連行を選択します。  
  
2.  行をダブルクリックして、**\[関連付けエディター\]** ダイアログ ボックスを開きます。  
  
3.  **\[関連付けのプロパティ\]** からプロパティを削除します。  
  
4.  プロパティの削除を再試行します。  
  
## 参照  
 [O\/R Designer Overview](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [How to: Create an Association \(Relationship\) Between LINQ to SQL Classes \(O\/R Designer\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)