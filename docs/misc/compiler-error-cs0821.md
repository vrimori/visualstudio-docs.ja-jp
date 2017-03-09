---
title: "コンパイラ エラー CS0821 | Microsoft Docs"
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
  - "CS0821"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0821"
ms.assetid: ef449115-93e8-4fa5-848a-d30dc7f68ddf
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0821
暗黙的に型指定されたローカル変数は修正できません  
  
 暗黙的に型指定されたローカル変数と匿名型は、`fixed` コンテキストではサポートされません。  
  
### このエラーを解決するには  
  
1.  変数から `fixed` 修飾子を削除するか、変数を明示的な型として指定します。  
  
## 使用例  
 次のコードでは CS0821 が生成されます。  
  
```  
class A { static int x; public static int Main() { unsafe { fixed (var p = &x) { } } return -1; } }  
```  
  
## 参照  
 [暗黙的に型指定されるローカル変数](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)