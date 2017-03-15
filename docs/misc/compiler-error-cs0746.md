---
title: "コンパイラ エラー CS0746 | Microsoft Docs"
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
  - "CS0746"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0746"
ms.assetid: 36baf7f2-b092-422c-ab53-95154bfceb0a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0746
匿名型のメンバー宣言子が無効です。 メンバー割り当て、簡易名、またはメンバー アクセスを使用して、匿名型メンバーを宣言する必要があります。  
  
 メンバー割り当て、簡易名、またはメンバー アクセスを使用して、匿名型を宣言する必要があります。  
  
### このエラーを解決するには  
  
1.  宣言で、メンバー割り当て、簡易名、またはメンバー アクセスの各表現のみを使用していることを確認します。  
  
## 使用例  
 次のコードでは、`incorrect_1` と `incorrect_2` の宣言で CS0746 が生成されます。 その次の宣言は、匿名型を宣言する 2 つの正しい方法を示しています。  
  
```  
// cs0746.cs public class C { public static int Main() { int i = 100; string s = "Bottles of beer."; var incorrect_1 = new { a.b = 1 }; // CS0746 var incorrect_2 = new {100, "Bottles of beer."}; // CS0746 var correct_1 = new { i, s }; //OK var correct_2 = new {num = i, message = s}; // OK return 1; } }  
  
```  
  
## 参照  
 [匿名型](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)