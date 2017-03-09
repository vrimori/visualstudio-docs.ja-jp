---
title: "コンパイラ エラー CS2019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2019"
ms.assetid: eafd2531-8b3a-499c-9e12-a605a011396f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS2019
\/target のターゲット型が無効です。'exe'、'winexe'、'library'、または 'module' のいずれかを指定してください。  
  
 [\/target](/dotnet/csharp/language-reference/compiler-options/target-compiler-option) コンパイラ オプションを使用していましたが、無効なパラメーターが渡されました。 このエラーを解決するには、出力ファイルに適切な **\/target** オプションの形式を使用してプログラムを再コンパイルします。  
  
 次の例では CS2017 が生成されます。  
  
```  
// CS2019.cs // compile with: /target:libra // CS2019 expected class MyClass { }  
```