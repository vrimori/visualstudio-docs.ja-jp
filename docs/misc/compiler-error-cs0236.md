---
title: "コンパイラ エラー CS0236 | Microsoft Docs"
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
  - "CS0236"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0236"
ms.assetid: 1522c421-744f-441f-9e05-6bb31311ab2a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0236
フィールド初期化子は、静的でないフィールド、メソッド、またはプロパティ 'field' を参照できません  
  
 インスタンス フィールドを使用して、メソッドの外部にある他のインスタンス フィールドを初期化することはできません。 メソッドの外部にある変数を初期化する場合には、クラス コンストラクター内で初期化を実行することをご検討ください。 詳細については、「[メソッド](/dotnet/csharp/programming-guide/classes-and-structs/methods)」を参照してください。  
  
 次の例では CS0236 が生成されます。  
  
```  
// CS0236.cs public class MyClass { public int i = 5; public int j = i;  // CS0236 public int k;      // initialize in constructor MyClass() { k = i; } public static void Main() { } }  
```