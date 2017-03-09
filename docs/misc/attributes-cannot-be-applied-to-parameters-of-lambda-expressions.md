---
title: "ラムダ式のパラメーターに属性を適用することはできません | Microsoft Docs"
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
  - "vbc36634"
  - "bc36634"
helpviewer_keywords: 
  - "BC36634"
ms.assetid: ed751d8d-11b7-4210-97e0-0319edff8c34
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ラムダ式のパラメーターに属性を適用することはできません
ラムダ式定義のパラメーターに属性を適用していますが、これはサポートされていません。 このエラーが発生するコード例を次に示します。  
  
```vb#  
Sub LambaAttribute()  
    ' Not valid.  
    Dim add1 = _  
    Function(<System.Runtime.InteropServices.InAttribute()> m As Integer) _  
                   m + 1  
End Sub  
```  
  
 **エラー ID:** BC36634  
  
### このエラーを解決するには  
  
-   属性を削除するか、ラムダ式を通常の関数に変更してコードを修正します。  
  
## 参照  
 <xref:System.Runtime.InteropServices.InAttribute>   
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)