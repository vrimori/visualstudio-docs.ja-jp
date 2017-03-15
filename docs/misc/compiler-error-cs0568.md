---
title: "コンパイラ エラー CS0568 | Microsoft Docs"
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
  - "CS0568"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0568"
ms.assetid: dc9e1263-f58d-4c95-9165-27ba7757bc7b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0568
構造体に明示的なパラメーターのないコンストラクターを含めることはできません。  
  
 各[構造体](/dotnet/csharp/language-reference/keywords/struct)には、既にオブジェクトをゼロに初期化する既定のコンストラクターがあります。 そのため、構造体に対して作成するコンストラクターは、1 つ以上のパラメーターを受け取る必要があります。  
  
 次の例では CS0568 が生成されます。  
  
```  
// CS0568.cs public struct ClassY { public int field1; public ClassY(){}   // CS0568, cannot have no param constructor // Try following instead: // public ClassY(int i) // { //    field1 = i; // } } public class ClassX { public static void Main() { } }  
```