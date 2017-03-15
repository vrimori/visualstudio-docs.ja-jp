---
title: "部分メソッド &#39;&lt;methodname2&gt;&#39; を実装するためには、メソッド &#39;&lt;methodname1&gt;&#39; を &#39;Private&#39; として宣言しなければなりません | Microsoft Docs"
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
  - "vbc31441"
  - "bc31441"
helpviewer_keywords: 
  - "BC31441"
ms.assetid: 4d8d19ad-0c3b-4eba-ada8-2cfa6ae795c4
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 部分メソッド &#39;&lt;methodname2&gt;&#39; を実装するためには、メソッド &#39;&lt;methodname1&gt;&#39; を &#39;Private&#39; として宣言しなければなりません
部分メソッドの実装は、`Private` として宣言する必要があります。 たとえば、次のコードでは、このエラーが発生します。  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub valueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' Implementation of the partial method, with Private missing, ' causes this error. 'Sub valueChanged() '    MsgBox(Value was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **エラー ID:** BC31441  
  
### このエラーを解決するには  
  
1.  次の例に示すように、部分メソッドの実装でアクセス修飾子 `Private` を使用します。  
  
    ```vb#  
    Private Sub valueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub  
    ```  
  
## 参照  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)