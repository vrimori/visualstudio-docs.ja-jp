---
title: "コンパイラの警告 (レベル 2) CS0278 | Microsoft Docs"
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
  - "CS0278"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0278"
ms.assetid: 5418cbbe-bcec-4379-a6f6-410987beb96a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0278
'type' は、'pattern name' パターンを実装しません。 'method name' があいまいなため、'method name' と混同します。  
  
 C\# には、`foreach` や `using` など、あらかじめ定義されたパターンを使用するステートメントがいくつかあります。 たとえば、`foreach` には、"列挙可能な" パターンを実装したコレクション クラスが使用されます。  
  
 CS0278 は、あいまいな部分があるために、コンパイラが適切な仲介処理を実行できない場合に発生する可能性があります。 たとえば、"列挙可能な" パターンを処理するためには、`MoveNext` というメソッドが必要ですが、コンパイルの対象になるコードには、`MoveNext` メソッドが 2 つ存在している可能性があります。 コンパイラは、どちらのインターフェイスを使用するかについて検索を試行しますが、あいまいさの原因を突き止め、解決することをお勧めします。  
  
 詳細については、「[方法 : foreach を使用してコレクション クラスにアクセスする](../Topic/How%20to:%20Access%20a%20Collection%20Class%20with%20foreach%20\(C%23%20Programming%20Guide\).md)」を参照してください。  
  
## 使用例  
 次の例では CS0278 が生成されます。  
  
```  
// CS0278.cs using System.Collections.Generic; public class myTest { public static void TestForeach<W>(W w) where W: IEnumerable<int>, IEnumerable<string> { foreach (int i in w) {}   // CS0278 } }  
```