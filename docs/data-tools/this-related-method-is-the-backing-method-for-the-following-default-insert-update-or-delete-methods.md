---
title: "This related method is the backing method for the following default insert, update, or delete methods | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# This related method is the backing method for the following default insert, update, or delete methods
この関連メソッドは、次の既定の挿入、更新、または削除メソッドのバッキング メソッドです。削除されると、これらのメソッドも削除されます。続行しますか?  
  
 選択した `DataContext` メソッドは、O\/R デザイナーで、いずれかのエンティティ クラスの挿入、更新、または削除メソッドとして現在使用されています。選択したメソッドを削除すると、このメソッドを使用していたエンティティ クラスの更新時の挿入、更新、または削除の動作は、既定のランタイムの動作に戻ることになります。  
  
### 選択したメソッドを削除して、エンティティ クラスでランタイムの更新動作が使用されるようにするには  
  
-   **\[はい\]** をクリックします。  
  
     選択されたメソッドが削除され、このメソッドを使用して更新動作をオーバーライドしていたすべてのクラスは、既定の LINQ to SQL ランタイムの動作を使用するように戻されます。  
  
### メッセージ ボックスを閉じて、選択したメソッドが変更されないようにするには  
  
-   **\[いいえ\]** をクリックします。  
  
     メッセージ ボックスが閉じ、変更は行われません。  
  
## 参照  
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [O\/R Designer Overview](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)