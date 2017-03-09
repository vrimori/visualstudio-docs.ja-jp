---
title: "コンパイラ エラー CS0017 | Microsoft Docs"
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
  - "CS0017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0017"
ms.assetid: 5e2a3eb3-6f6e-485d-8293-ceabea4d6905
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0017
プログラム 'output file name' に、複数のエントリ ポイントが定義されています。 エントリ ポイントを含む型を指定するために、\/main を使用してコンパイルします。  
  
 プログラムには、[Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) メソッドを 1 つのみ指定できます。  
  
 このエラーを解決するには、Main メソッドを 1 つのみコードに残して残りをすべてコードから削除するか、[\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) コンパイラ オプションを使用してどの Main メソッドを使用するか指定できます。  
  
 次の例では CS0017 が生成されます。  
  
```  
// CS0017.cs // compile with: /target:exe public class clx { static public void Main() { } } public class cly { public static void Main()   // CS0017, delete one Main or use /main { } }  
```