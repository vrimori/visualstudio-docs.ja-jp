---
title: "定数式の先頭で &#39;.&#39; または &#39;!&#39; を使用することはできません | Microsoft Docs"
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
  - "vbc30995"
  - "bc30995"
helpviewer_keywords: 
  - "BC30995"
ms.assetid: eed62684-66db-4fdb-9da7-f1407a55b172
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 定数式の先頭で &#39;.&#39; または &#39;!&#39; を使用することはできません
メンバー アクセス \(.\) およびディクショナリ メンバー アクセス \(\!\) では、ほとんどの場合、メンバが含まれている要素を指定した式が必要になります。定数式の場合もそうです。 次の宣言は無効です。  
  
```  
' Not valid. Const c As String = .name  
```  
  
 **エラー ID:** BC30995  
  
### このエラーを解決するには  
  
-   アクセスするメンバーが含まれているインスタンスを指定します。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [方法: 匿名型のインスタンスを宣言する \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)