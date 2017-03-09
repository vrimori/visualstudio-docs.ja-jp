---
title: "コンパイラの警告 (レベル 4) CS0028 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0028"
ms.assetid: 47df919f-01fa-45ae-a4b7-912445e679e2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 4) CS0028
'function declaration' で間違った認証が使われています。エントリ ポイントとして使用することはできません  
  
 `Main` のメソッド宣言は無効です。無効なシグネチャで宣言されました。`Main` は静的として宣言され、[int](/dotnet/csharp/language-reference/keywords/int) または [void](/dotnet/csharp/language-reference/keywords/void) を返す必要があります。 詳細については、「[Main\(\) とコマンド ライン引数](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments)」を参照してください。  
  
 次の例では CS0028 が生成されます。  
  
```  
// CS0028.cs // compile with: /W:4 /warnaserror public class a { public static double Main(int i)   // CS0028 // Try the following line instead: // public static void Main() { } }  
```