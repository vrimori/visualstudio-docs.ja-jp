---
title: "&#39;ByRef&#39; パラメーター &#39;&lt;parametername&gt;&#39; をラムダ式で使用することはできません | Microsoft Docs"
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
  - "bc36639"
  - "vbc36639"
helpviewer_keywords: 
  - "BC36639"
ms.assetid: 5913f9b6-2929-4c05-8dd1-00b10fcd5a83
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ByRef&#39; パラメーター &#39;&lt;parametername&gt;&#39; をラムダ式で使用することはできません
`Sub` または関数の中で宣言したラムダ式では、その `Sub` または関数の `ByRef` パラメーターを使用できません。 たとえば、以下のコードでは、ラムダ式で `ByRef` パラメーター `n` を使用しているので、このエラーが発生します。  
  
```  
'' Not valid.   
'Sub ExampleSub(ByRef n As Integer)  
  
'    Dim lambda = Function(p As Integer) p + n  
  
'End Sub  
```  
  
 **エラー ID:** BC36639  
  
### このエラーを解決するには  
  
-   次のコードに示すように、`ByRef` パラメーターをローカル変数に割り当てて、そのローカル変数をラムダ式で使用します。  
  
    ```  
    Sub ExampleSub(ByRef n As Integer)  
  
        Dim temp = n  
        Dim lambda = Function(p As Integer) p + temp  
  
    End Sub  
    ```  
  
## 参照  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)