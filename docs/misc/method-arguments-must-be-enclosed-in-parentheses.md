---
title: "メソッドの引数は、かっこで囲む必要があります。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30800"
  - "bc30800"
helpviewer_keywords: 
  - "BC30800"
ms.assetid: ecdec760-8b51-474f-acad-17cf8059d83b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッドの引数は、かっこで囲む必要があります。
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の最近のバージョンでは、プロシージャ呼び出しを制御する規則が単純になっています。 すべての引数はかっこで囲む必要があります。  
  
 **エラー ID:** BC30800  
  
### このエラーを解決するには  
  
-   引数リストをかっこで囲みます。次に例を示します。  
  
    ```  
    MySub(ArrayIndex, NewValue)  
    ```  
  
## 参照  
 [Procedure Calling Sequence Changes in Visual Basic](http://msdn.microsoft.com/ja-jp/4ef1eea6-36cb-4b97-a31b-9ba65e46a9fd)   
 [Procedure Parameters and Arguments](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)