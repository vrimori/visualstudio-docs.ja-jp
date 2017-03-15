---
title: "&#39;Set&#39; パラメーターの型は、それを含むプロパティと同じ型でなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31064"
  - "bc31064"
helpviewer_keywords: 
  - "BC31064"
ms.assetid: f0b8310d-68a1-4989-ac64-03b1861528ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Set&#39; パラメーターの型は、それを含むプロパティと同じ型でなければなりません
`Set` プロパティ プロシージャのパラメーターは自身が属しているプロパティとは異なる型です。  
  
 **エラー ID:** BC31064  
  
### このエラーを解決するには  
  
-   パラメーターのデータ型を `Set` に変更して、プロパティのデータ型と一致するようにします。 例:  
  
    ```  
    Class Class1 ' Declare a local variable to hold the property value. Private Fval As Integer Property F() As Integer Get Return Fval End Get Set(ByVal Value As Integer) Fval = Value End Set End Property End Class  
    ```  
  
## 参照  
 [ビルド内にありません: 方法: フィールドとプロパティをクラスに追加する](http://msdn.microsoft.com/ja-jp/ae53f61b-3abc-413e-8931-703c5f5e8fc2)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [ビルド内にありません: プロパティと Property プロシージャ](http://msdn.microsoft.com/ja-jp/23e2a1ec-7e9d-4109-8940-c703d981077b)