---
title: "Option Strict On では、メソッド &#39;&lt;methodname&gt;&#39; とデリゲート &#39;&lt;delegatename&gt;&#39; の間の暗黙的な型の変換で縮小変換を許可していません。 | Microsoft Docs"
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
  - "bc36663"
  - "vbc36663"
helpviewer_keywords: 
  - "BC36663"
ms.assetid: fefc7ab5-b587-4ff9-a6bc-4c4e5d4b6b29
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、メソッド &#39;&lt;methodname&gt;&#39; とデリゲート &#39;&lt;delegatename&gt;&#39; の間の暗黙的な型の変換で縮小変換を許可していません。
`Option Strict` がオンの場合、デリゲート内のパラメーターのデータ型と、そのデリゲート型の変数に割り当てられている関数または `Sub` の対応するパラメーターの間で縮小変換することはできません。 たとえば、関数デリゲート `Del` には型 `Integer` のパラメーターが 1 つあり、関数 `Conversion1`、`Conversion2`、および `Conversion3` には異なる数値型のパラメーターが 1 つあります。  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String Function Conversion1(ByVal n As Integer) As String Return "Valid" End Function Function Conversion2(ByVal n As Long) As String Return "Valid" End Function Function Conversion3(ByVal n As Short) As String Return "Not valid" End Function  
```  
  
 `Integer` から `Integer` および `Long` への拡大変換があるので、次の割り当ては有効です。  
  
```vb#  
' Valid. Dim funDel1 As Del = AddressOf Conversion1 Dim funDel2 As Del = AddressOf Conversion2  
```  
  
 `Integer` から `Short` への変換は縮小変換です。 したがって、次の割り当ては有効ではありません。  
  
```vb#  
' Not valid. Dim funDel3 As Del = AddressOf Conversion3  
```  
  
 エラー ID: BC36663  
  
### このエラーを解決するには  
  
-   デリゲートまたはメソッドのパラメーターのデータ型を変更して、必要な拡大関係が存在するようにします。  
  
## 参照  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)