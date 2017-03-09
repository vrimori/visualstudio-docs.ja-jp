---
title: "The objects you are adding to the designer use a different data connection than the designer is currently using | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The objects you are adding to the designer use a different data connection than the designer is currently using
デザイナーに追加する対象のオブジェクトは、デザイナーが現在使用しているのとは異なるデータ接続を使用しています。デザイナーが使用している接続に置き換えますか?  
  
 [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) に項目を追加するときは、すべての項目で 1 つの共有データ接続が使用されます。デザイン サーフェイスは、サーフェイス上のすべてのオブジェクトに対して単一の接続を使用する <xref:System.Data.Linq.DataContext> を表します。デザイナーで現在使用されているデータ接続とは異なるデータ接続を使用するオブジェクトをデザイナーに追加すると、このメッセージが表示されます。このエラーを解決するために、既存の接続を維持するように選択できます。その場合、選択したオブジェクトは追加されません。別の方法として、オブジェクトを追加し、<xref:System.Data.Linq.DataContext> 接続を新しい接続にリセットすることもできます。  
  
> [!NOTE]
>  **\[はい\]** をクリックすると、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]のすべてのエンティティ クラスが新しい接続にマップされます。  
  
### 選択したオブジェクトで使用されている接続で既存の接続を置換するには  
  
-   **\[はい\]** をクリックします。  
  
     選択したオブジェクトが [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加され、DataContext.Connection が新しい接続に設定されます。  
  
### 既存の接続を引き続き使用し、選択したオブジェクトの追加を取り消すには  
  
-   **\[いいえ\]** をクリックします。  
  
     操作がキャンセルされます。DataContext.Connection は、既存の接続に設定されたままになります。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)