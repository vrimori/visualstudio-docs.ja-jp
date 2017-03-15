---
title: "コンパイラ エラー CS0463 | Microsoft Docs"
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
  - "CS0463"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0463"
ms.assetid: 0cb4be4e-86ea-4ade-8817-b17d4cacd4d5
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0463
10 進数の定数式の評価に失敗し、次のエラーが発生しました: 'error'  
  
 このエラーは、10 進数の定数式がコンパイル時にオーバーフローした場合に発生します。  
  
 通常、実行時にオーバーフロー エラーが発生します。 この場合、コンパイラが結果を評価し、オーバーフローが発生することを認識するように定数式を定義しています。  
  
## 使用例  
 次のコードではエラー CS0463 が生成されます。  
  
```  
// CS0463.cs using System; class MyClass { public static void Main() { const decimal myDec = 79000000000000000000000000000.0m + 79000000000000000000000000000.0m; // CS0463 Console.WriteLine(myDec.ToString()); } }  
```