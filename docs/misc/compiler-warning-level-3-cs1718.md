---
title: "コンパイラの警告 (レベル 3) CS1718 | Microsoft Docs"
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
  - "CS1718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1718"
ms.assetid: 7c1c11fd-4f91-482d-b8f7-efe2a361634e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS1718
同じ変数と比較されました。他の変数と比較しますか?  
  
 別のものと比較する場合は、単にステートメントを修正する必要があります。  
  
 あるいは、`if (a == a) (true)` や `if (a < a) (false)` などのステートメントによって真または偽のテストを実施しようとした可能性もあります。 単に `if (true)` や `if (false)` とする方が適切です。 これには、次の 2 つの理由があります。  
  
-   こちらの方が簡単です。率直な表現の方が常に明快になります。  
  
-   混乱の回避に役立ちます。C\# 2.0 の新機能は Null 許容の値型ですが、これは T\-SQL \(SQL Server で使用するプログラミング言語\) の値 `null` に似ています。 T\-SQL では三値論理を使用するため、T\-SQL に慣れた開発者は、Null 許容型が `if (a == a)` などの式に及ぼす影響について懸念する可能性があります。`true` または `false` を使用すると、このような混乱を避けることができます。  
  
## 使用例  
 次のコードでは、警告 CS1718 が生成されます。  
  
```  
// CS1718.cs using System; public class Tester { public static void Main() { int i = 0; if (i == i) { // CS1718.cs //if (true) { i++; } } }  
```