---
title: "How to: Turn Pluralization On and Off (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Turn Pluralization On and Off (O/R Designer)
既定では、名前が s または ies で終わるデータベース オブジェクトを**サーバー エクスプローラー**または**データベース エクスプローラー**から[Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) にドラッグすると、生成されるエンティティ クラスの名前が複数形から単数形に変更されます。この処理は、インスタンス化されたエンティティ クラスが単一のデータ レコードにマップされるという事実をより正確に表すために行われます。たとえば、Customers テーブルを [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加すると、Customer という名前のエンティティ クラスが生成されます。このクラスには、単一の顧客のみが保持されるためです。  
  
> [!NOTE]
>  複数形化は、英語バージョンの Visual Studio でのみ、既定でオンになります。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 複数形化をオンまたはオフにするには  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[オプション\]** ダイアログ ボックスの **\[データベース ツール\]** を展開します。  
  
> [!NOTE]
>  **\[データベース ツール\]** ノードが表示されない場合は、**\[すべての設定を表示\]** を選択します。  
  
1.  **\[O\/R デザイナー\]** をクリックします。  
  
2.  **\[名前の複数形化\]** で **\[有効\]** を **\[False\]** に設定すると、クラス名を変更しないように [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]が設定されます。  
  
3.  **\[名前の複数形化\]** で **\[有効\]** を **\[True\]** に設定すると、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に追加されるオブジェクトのクラス名に複数形化規則が適用されます。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)