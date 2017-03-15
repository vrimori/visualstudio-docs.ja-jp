---
title: "&#39;Inherits&#39; は、&#39;Class&#39; ステートメント内で 1 回のみ使用でき、1 つのクラスのみを指定できます | Microsoft Docs"
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
  - "vbc30121"
  - "bc30121"
helpviewer_keywords: 
  - "BC30121"
ms.assetid: 4ac5b018-5632-4661-8ac6-dbda2f8c4dfe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Inherits&#39; は、&#39;Class&#39; ステートメント内で 1 回のみ使用でき、1 つのクラスのみを指定できます
同じクラスに複数の `Inherits` ステートメントを記述しているか、または `Inherits` ステートメントに複数のクラスを指定しています。 クラスは、1 つの基底クラスのみから継承できます。  
  
 **エラー ID:** BC30121  
  
### このエラーを解決するには  
  
-   余分な `Inherits` ステートメントを削除し、残りの `Inherits` ステートメントに基底クラスを 1 つのみ指定していることを確認します。  
  
## 参照  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)