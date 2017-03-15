---
title: "型パラメーター &#39;&lt;typeparametername&gt;&#39; を推論できません。 | Microsoft Docs"
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
  - "bc36572"
  - "vbc36572"
helpviewer_keywords: 
  - "BC36572"
ms.assetid: 02264070-b055-4ab0-8d2a-eac4d90d9fdf
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター &#39;&lt;typeparametername&gt;&#39; を推論できません。
型引数リストの指定なくジェネリック プロシージャが呼び出され、型引数のいずれかについて型の推定が失敗します。  
  
 ジェネリック プロシージャを呼び出す場合、通常、型パラメーターごとにプロシージャで定義されている型引数を指定します。 ただし、型引数リストをすべて省略することもできます。 これを行う場合、コンパイラでは、呼び出しのコンテキストから、型引数ごとに型の推論が試行されます。 詳細については、「[Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)」の「型の推定」を参照してください。  
  
 **エラー ID:** BC36572  
  
### このエラーを解決するには  
  
-   型の推定がジェネリック プロシージャに宣言された型パラメーターと一致するような、標準的な引数の型が指定されていることを確認します。  
  
     または  
  
-   型の推定の必要がなくなるように、完全な型引数リストを使用したジェネリック プロシージャを呼び出します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)