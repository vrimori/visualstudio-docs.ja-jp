---
title: "&#39;&lt;membername&gt;&#39; を複数回初期化しています | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30989"
  - "bc30989"
helpviewer_keywords: 
  - "BC30989"
ms.assetid: 574b6398-1e9d-43e1-ac16-6fc8687f71d9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; を複数回初期化しています
'\<membername\>' を複数回初期化しています。 フィールドおよびプロパティは、オブジェクト初期化子式で 1 回しか初期化できません。  
  
 オブジェクト初期化子リストで各フィールドおよびプロパティに初期値を割り当てることができるのは 1 回だけです。 次の宣言は無効です。  
  
```  
' Dim cust = New Customer() With {.Name = "Bob", .Name = "Robert"}  
```  
  
> [!NOTE]
>  次の宣言に示されているように、別のメンバーの初期値として 1 つのフィールドまたはプロパティを使用できます。  
  
```  
Dim cust = New Customer() With {.First = "Mike", .Last = "Nash", _ .Full = .First & " " & .Last}  
```  
  
 **エラー ID:** BC30989  
  
### このエラーを解決するには  
  
-   オブジェクト初期化子リスト内のフィールドまたはプロパティごとに、初期化を 1 つだけ残して、後はすべて削除します。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [ビルド内にありません: プロパティ プロシージャとフィールド](http://msdn.microsoft.com/ja-jp/da1c05c1-87c7-40fa-b92c-e9c7e4d170f7)