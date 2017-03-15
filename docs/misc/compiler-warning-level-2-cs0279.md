---
title: "コンパイラの警告 (レベル 2) CS0279 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0279"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0279"
ms.assetid: 5e5faa8f-3d5b-4999-aa62-ff7f131a3e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0279
'type name' は 'pattern name' パターンを実装しません。 'method name' が静的であるか、パブリックではありません。  
  
 C\# には、`foreach` や `using` など、あらかじめ定義されたパターンを使用するステートメントがいくつかあります。 たとえば、`foreach` には、列挙可能なパターンを実装したコレクション クラスが使用されます。 このエラーは、`static` として宣言されているか `public` でないとして宣言されているメソッドが原因で、コンパイラが照合を処理できないときに発生します。 パターン内のメソッドは、クラスのインスタンスであり、パブリックであることが必要です。  
  
## 使用例  
 次の例では、CS0279 が生成されます。  
  
```  
// CS0279.cs using System; using System.Collections; public class myTest : IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } public static void Main() { foreach (int i in new myTest()) {}  // CS0279 } }  
```