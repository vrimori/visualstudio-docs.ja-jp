---
title: "パラメーター名 &#39;&lt;parametername1&gt;&#39; は、部分メソッドの宣言 &#39;&lt;methodname&gt;&#39; で定義された、対応するパラメーターの名前 &#39;&lt;parametername2&gt;&#39; と一致しません | Microsoft Docs"
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
  - "vbc31442"
  - "bc31442"
helpviewer_keywords: 
  - "BC31442"
ms.assetid: 7f097bb2-071a-42ec-b7af-40da04f602f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# パラメーター名 &#39;&lt;parametername1&gt;&#39; は、部分メソッドの宣言 &#39;&lt;methodname&gt;&#39; で定義された、対応するパラメーターの名前 &#39;&lt;parametername2&gt;&#39; と一致しません
部分メソッドの宣言と実装に対してパラメーターを指定するときは、対応するパラメーターの名前を同じにする必要があります。 たとえば、次のコードでは、このエラーが発生します。  
  
```vb#  
Partial Class Product  
  
    ' Declaration of the partial method.  
    Partial Private Sub valueChanged(ByVal newVal As Integer)  
    End Sub  
End Class  
```  
  
```vb#  
Partial Class Product  
  
    ' Implementation of the partial method. This error is  
    ' reported for parameter val.  
    ' Private Sub valueChanged(ByVal val As Integer)  
    '     MsgBox(Value was changed to " & Me.Quantity)  
    ' End Sub  
  
End Class  
```  
  
 **エラー ID:** BC31442  
  
### このエラーを解決するには  
  
1.  対応するパラメーターが同じ名前になるように、宣言または実装のパラメーター名を変更します。  
  
## 参照  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)