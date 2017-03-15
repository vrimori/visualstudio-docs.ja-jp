---
title: "メソッド &#39;&lt;methodname&gt;&#39; に、デリゲート &lt;&#39;delegatename&#39;&gt; と互換性があるシグネチャがありません | Microsoft Docs"
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
  - "vbc31143"
  - "bc31143"
helpviewer_keywords: 
  - "BC31143"
ms.assetid: 88990637-7c92-467e-a3d3-db5498dc1dce
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド &#39;&lt;methodname&gt;&#39; に、デリゲート &lt;&#39;delegatename&#39;&gt; と互換性があるシグネチャがありません
このエラーは、メソッドとデリゲート間で必要な変換ができない場合に生じます。 エラーの原因としては、パラメーターの間の変換か、戻り値の変換 \(メソッドとデリゲートが関数の場合\) が考えられます。  
  
 次のコードは、こうした障害が発生する変換を示しています。 デリゲートは `FunDel` です。  
  
```vb#  
Delegate Function FunDel(ByVal i As Integer, ByVal d As Double) As Integer  
```  
  
 次の関数は、このエラーを生じさせる原因が `FunDel` とはそれぞれ異なります。  
  
```vb#  
Function ExampleMethod1(ByVal m As Integer, ByVal aDate As Date) As Integer End Function Function ExampleMethod2(ByVal m As Integer, ByVal aDouble As Double) As Date End Function  
```  
  
 次のそれぞれの代入ステートメントでもエラーが発生します。  
  
```vb#  
Sub Main() ' The second parameters of FunDel and ExampleMethod1, Double and Date, ' are not compatible. 'Dim d1 As FunDel = AddressOf ExampleMethod1 ' The return types of FunDel and ExampleMethod2, Integer and Date, ' are not compatible. 'Dim d2 As FunDel = AddressOf ExampleMethod2 End Sub  
```  
  
 **エラー ID:** BC31143  
  
### このエラーを解決するには  
  
-   対応するパラメーター、および戻り値の型 \(存在する場合\) を調べて、互換性のないペアを特定します。  
  
## 参照  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)