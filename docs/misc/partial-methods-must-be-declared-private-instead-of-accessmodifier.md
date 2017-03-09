---
title: "部分メソッドは、&#39;&lt;accessModifier&gt;&#39; ではなく &#39;Private&#39; と宣言しなければなりません | Microsoft Docs"
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
  - "vbc31431"
  - "bc31431"
helpviewer_keywords: 
  - "BC31431"
ms.assetid: bbd757f3-7281-4488-8a06-f3b4bcc820dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 部分メソッドは、&#39;&lt;accessModifier&gt;&#39; ではなく &#39;Private&#39; と宣言しなければなりません
アクセス修飾子 `Private` は部分メソッドの宣言に必要です。 メソッドのシグネチャとその実装で `Private` を使用する例を次に示します。  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **エラー ID:** BC31431  
  
### このエラーを解決するには  
  
-   シグネチャと実装の宣言で、アクセス修飾子を `Private` に変更します。  
  
## 参照  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)