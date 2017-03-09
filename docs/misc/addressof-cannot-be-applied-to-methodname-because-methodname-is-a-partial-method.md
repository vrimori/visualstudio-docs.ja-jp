---
title: "&#39;methodname&#39; は部分メソッドであるため、&#39;AddressOf&#39; を &#39;methodname&#39; に適用できません | Microsoft Docs"
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
  - "vbc31440"
  - "bc31440"
helpviewer_keywords: 
  - "BC31440"
ms.assetid: 924dbada-3e0a-4004-a3ae-a209b7c3d1fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;methodname&#39; は部分メソッドであるため、&#39;AddressOf&#39; を &#39;methodname&#39; に適用できません
`AddressOf` 演算子に部分メソッドが渡されました。`AddressOf` 演算子に対して部分メソッドは無効な値です。  
  
 **エラー ID:** BC31440  
  
### このエラーを解決するには  
  
1.  部分メソッドに対する実装メソッドを追加します。 実装メソッドは `AddressOf` 演算子に対して有効な値です。 次の例では、部分メソッドのシグネチャとその実装を示します。  
  
    ```vb#  
    ' Definition of the partial method signature.  
    Partial Private Sub OnNameChanged()  
        ' The body of the signature is empty.  
    End Sub  
  
    ' Implementation of the partial method.  
    Private Sub OnNameChanged()  
        MsgBox("Name was changed to " & Me.Name)  
    End Sub  
    ```  
  
## 参照  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)