---
title: "メソッド &#39;&lt;methodname1&gt;&#39; は部分メソッド &#39;&lt;methodname2&gt;&#39; を実装できません。このメソッドは既に &#39;&lt;methodname3&gt;&#39; が実装しています | Microsoft Docs"
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
  - "vbc31434"
  - "bc31434"
helpviewer_keywords: 
  - "BC31434"
ms.assetid: 61cba19e-db11-4a06-89d6-4244d411588c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド &#39;&lt;methodname1&gt;&#39; は部分メソッド &#39;&lt;methodname2&gt;&#39; を実装できません。このメソッドは既に &#39;&lt;methodname3&gt;&#39; が実装しています
メソッド '\<methodname1\>' は部分メソッド '\<methodname2\>' を実装できません。このメソッドは既に '\<methodname3\>' が実装しています。 部分メソッドを実装できるのは、1 つのメソッドのみです。  
  
 同じ部分メソッドの宣言を実装する 2 つの部分メソッドがあってはなりません。 次のコードを使用すると、このエラーが発生します。  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub ValueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' First implementation of the partial method. Private Sub ValueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub ' Second implementation of the partial method causes this error. 'Private Sub ValueChanged() '    Console.WriteLine("Quantity was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **エラー ID:** BC31434  
  
## 参照  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)