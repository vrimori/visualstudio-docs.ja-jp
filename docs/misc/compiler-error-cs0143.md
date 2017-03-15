---
title: "コンパイラ エラー CS0143 | Microsoft Docs"
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
  - "CS0143"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0143"
ms.assetid: dfe6f6ba-dec9-49bd-9d5b-3dc4743bd940
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0143
型 'class' のコンストラクターが定義されていません  
  
 使用できる適切なコンストラクターがありません。 これが該当するのは、値を代入するだけで初期化される、組み込みの数値型の場合です。  
  
 次の例では CS0143 が生成されます。  
  
```  
// CS0143.cs class MyClass { static public void Main () { double d = new double(4.5);   // CS0143 // Try this line instead: // double d = 4.5; } }  
```