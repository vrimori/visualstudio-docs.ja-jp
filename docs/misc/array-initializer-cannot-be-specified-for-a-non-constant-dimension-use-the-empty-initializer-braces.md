---
title: "配列初期化子は非定数の次元に指定することはできません。空の初期化子 &#39;{}&#39; を使用してください | Microsoft Docs"
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
  - "vbc30949"
  - "bc30949"
helpviewer_keywords: 
  - "BC30949"
ms.assetid: b3d27d9c-7a1f-4bac-ad71-388b24b807b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列初期化子は非定数の次元に指定することはできません。空の初期化子 &#39;{}&#39; を使用してください
配列が、コンパイル時に知られていないディメンションを初期化します。  
  
 次のコードでは、このエラーが生成されます。  
  
```  
Dim j As Integer Dim intArray As Integer = New Integer(1, j) {{0, 100}, {1,101}}  
```  
  
 次のコードでは、エラーが回避されます。  
  
```  
Dim intArray As Integer = New Integer(1, j) {} For i As Integer = 0 To j intArray(0, i) = i intArray(1, i) = 100 + i Next i  
```  
  
 **エラー ID:** BC30949  
  
### このエラーを解決するには  
  
-   可能であれば、配列の宣言で定数の次元を指定します。  
  
-   定数の次元を指定できない場合は、非定数のディメンションがわかったときに、ループを使用して、配列を初期化する必要があります。  
  
## 参照  
 [For Each...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [ビルド内にありません: Visual Basic での配列の概要](http://msdn.microsoft.com/ja-jp/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [NOTINBUILD 方法: 多次元配列を初期化する](http://msdn.microsoft.com/ja-jp/502dcf8b-d86c-46f1-ad7d-3ce809645774)