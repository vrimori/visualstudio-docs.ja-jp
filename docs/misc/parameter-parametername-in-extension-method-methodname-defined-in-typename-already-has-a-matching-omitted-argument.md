---
title: "&#39;&lt;typename&gt;&#39; で定義された拡張メソッド &#39;&lt;methodname&gt;&#39; のパラメーター &#39;&lt;parametername&gt;&#39; には、一致する省略された引数が既に存在します。 | Microsoft Docs"
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
  - "bc36583"
  - "vbc36583"
helpviewer_keywords: 
  - "BC36583"
ms.assetid: 662072fa-abb8-43c3-8ca2-aefb20f2e902
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; で定義された拡張メソッド &#39;&lt;methodname&gt;&#39; のパラメーター &#39;&lt;parametername&gt;&#39; には、一致する省略された引数が既に存在します。
拡張メソッドへのプロシージャ呼び出しでは、位置による引数を省略し、名前で引数を指定します。 たとえば、拡張メソッド `ABC` への次の呼び出しでは、最初にパラメーター `Y` の引数を省略してから、名前で指定します。  
  
```  
<Extension()> _ Public Sub ABC(ByVal X As Integer, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) End Sub ' . . . ' Calling extension method ABC. Dim number As Integer ' Not valid. ' number.ABC(, 4, Y:=5)  
```  
  
 **エラー ID:** BC36583  
  
### このエラーを解決するには  
  
-   位置による引数を指定するか、または引数を省略するコンマを削除します。  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)