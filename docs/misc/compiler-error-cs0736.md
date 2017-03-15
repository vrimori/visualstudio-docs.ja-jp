---
title: "コンパイラ エラー CS0736 | Microsoft Docs"
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
  - "CS0736"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0736"
ms.assetid: 06b14feb-81d5-495f-ab2d-6dc3f5e7216f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0736
'type name' はインターフェイス メンバー 'member name' を実装しません。 'method name' は静的であるため、インターフェイス メンバーを実装できません。  
  
 このエラーは、インターフェイス メンバーの実装として静的メソッドが暗黙的または明示的に宣言されると生成されます。  
  
### このエラーを解決するには  
  
-   [static](/dotnet/csharp/language-reference/keywords/static) 修飾子を、メソッドの宣言から削除します。  
  
-   インターフェイス メソッドの名前を変更します。  
  
-   インターフェイスを継承しないように、含める型を再定義します。  
  
## 使用例  
 次のコードでは、`Program.testMethod` が静的として宣言されるため、CS0736 が生成されます。  
  
```  
// cs0736.cs namespace CS0736 { interface ITest { int testMethod(int x); } class Program : ITest // CS0736 { public static int testMethod(int x) { return 0; } // Try the following line instead. // public int testMethod(int x) { return 0; } public static void Main() { } } }  
```  
  
## 参照  
 [インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)