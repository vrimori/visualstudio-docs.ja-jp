---
title: "縮小変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な &#39;&lt;methodname&gt;&#39; はありません: &lt;list&gt; | Microsoft Docs"
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
  - "vbrAmbiguousCall2"
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 縮小変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な &#39;&lt;methodname&gt;&#39; はありません: &lt;list&gt;
オーバーロードされたメソッドが呼び出されましたが、メソッドは縮小変換せずに指定された引数のリストと一致しません。  
  
### このエラーを解決するには  
  
1.  `Option`  `Strict` `Off` を指定します。  
  
2.  オーバーロードされたメソッドのシグネチャと一致するように、引数を変更します。  
  
## 参照  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)