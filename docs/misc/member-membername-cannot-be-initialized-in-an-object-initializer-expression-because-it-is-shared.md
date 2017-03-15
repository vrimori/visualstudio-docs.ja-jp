---
title: "メンバー &#39;&lt;membername&gt;&#39; は共有されているため、オブジェクト初期化子式で初期化できません | Microsoft Docs"
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
  - "bc30991"
  - "vbc30991"
helpviewer_keywords: 
  - "BC30991"
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メンバー &#39;&lt;membername&gt;&#39; は共有されているため、オブジェクト初期化子式で初期化できません
オブジェクト初期化子を使用して、共有と宣言されているクラスのメンバーを初期化することはできません。 詳細については、「[Shared](/dotnet/visual-basic/language-reference/modifiers/shared)」を参照してください。  
  
 **エラー ID:** BC30991  
  
### このエラーを解決するには  
  
1.  クラス定義を確認して、共有されているメンバーを特定します。  
  
2.  オブジェクト初期化子リストから、そのメンバーの初期化を削除します。  
  
## 使用例  
 次の例では、`totalCustomers` が共有メンバーです。  
  
```  
Public Class Customer Public Shared totalCustomers As Integer ' Other declarations and method definitions. End Class  
```  
  
 `totalCustomers` は共有されているため、オブジェクト初期化子リストでその初期値を設定しようとすると、このエラーが発生します。  
  
```  
' This declaration is not valid. ' Dim cust As New Customer With { .Name = "Coho Winery", _ '                                 .totalCustomers = 21 }  
```  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [ビルド内にありません: Visual Basic の共有メンバー](http://msdn.microsoft.com/ja-jp/dbc3783f-83a2-4225-995d-c2d6d025663d)