---
title: "&#39;Throw&#39; オペランドは、&#39;System.Exception&#39; から派生しなければなりません | Microsoft Docs"
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
  - "vbc30665"
  - "bc30665"
helpviewer_keywords: 
  - "BC30665"
ms.assetid: 7c228087-39ea-4b30-a410-6ba711e67e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Throw&#39; オペランドは、&#39;System.Exception&#39; から派生しなければなりません
`Throw` に指定した引数は、`System.Exception` のインスタンスであるか、または `System.Exception` から派生したクラスのインスタンスである必要があります。  
  
 **エラー ID:** BC30665  
  
### このエラーを解決するには  
  
-   次の例のように、`System.Exception` から派生した引数を使用します。  
  
    ```  
    Throw New System.Exception("This is an error.")  
    ```  
  
## 参照  
 [Throw Statement](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic での例外クラス](http://msdn.microsoft.com/ja-jp/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Visual Basic での例外とエラー処理](http://msdn.microsoft.com/ja-jp/3e351e73-cf23-40ab-8b60-05794160529e)