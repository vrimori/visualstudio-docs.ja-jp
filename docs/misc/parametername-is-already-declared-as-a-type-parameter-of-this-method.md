---
title: "&#39;&lt;parametername&gt;&#39; は、このメソッドの型パラメーターとして既に宣言されています | Microsoft Docs"
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
  - "bc32089"
  - "vbc32089"
helpviewer_keywords: 
  - "BC32089"
ms.assetid: 5e440b4b-f62b-4ff5-9148-2372d4752bf6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;parametername&gt;&#39; は、このメソッドの型パラメーターとして既に宣言されています
ジェネリック プロシージャは、通常のパラメーターか、型パラメーターと同じ名前を持つローカル変数を定義します。  
  
 プロシージャのそれぞれのパラメーター \(ジェネリック プロシージャのそれぞれの型パラメーターを含む\) に、他のすべてのパラメーターと異なる名前を指定する必要があります。 プロシージャ パラメーターはローカル変数として使用されるため、プロシージャ内で宣言されるそれぞれのローカル変数には、すべてのパラメーターおよび型パラメーターと異なる名前を指定する必要があります。  
  
 **エラー ID:** BC32089  
  
### このエラーを解決するには  
  
-   通常のパラメーターまたはローカル変数の名前を変更します。  
  
## 参照  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Parameter List](/dotnet/visual-basic/language-reference/statements/parameter-list)