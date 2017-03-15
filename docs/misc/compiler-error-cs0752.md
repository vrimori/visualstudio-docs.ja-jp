---
title: "コンパイラ エラー CS0752 | Microsoft Docs"
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
  - "CS0752"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0752"
ms.assetid: f9a373d6-31ed-42db-8206-80cbe9b8c546
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0752
部分メソッドは、out パラメーターを含むことはできません  
  
 部分メソッドは、[out](/dotnet/csharp/language-reference/keywords/out) パラメーターを含むことはできません 部分メソッドがコンパイラによって削除された場合、out パラメーターが常に割り当てられる保証がないので、out パラメーターは許可されてません。  
  
### このエラーを解決するには  
  
1.  パラメーターから out 修飾子を削除し、代わりに、メソッドの戻り値を使用するか、メソッドの宣言から部分的な修飾子を削除します。  
  
## 使用例  
 次のコードでは CS0752 が生成されます。  
  
```  
// cs0752.cs public partial class C { partial void Part(out int num); // CS0752 // try the following line instead // partial void Part(int num); public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)