---
title: "コンパイラ エラー CS1110 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1110"
ms.assetid: 5b571a76-1891-4f33-b23d-7c4cc654a05f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1110
System.Core.dll への参照がないメソッド宣言の最初のパラメーターでは 'this' 修飾子を使用できません。 System.Core.dll への参照を追加するか、メソッド宣言から 'this' 修飾子を削除します。  
  
 拡張メソッドは、.NET Framework のバージョン 3.5 以降でされています。 拡張メソッドは、メソッドを属性でマークするメタデータを生成します。 属性クラスは、system.core.dll にあります。  
  
### このエラーを解決するには  
  
1.  メッセージにあるように、System.Core.dll への参照を追加するか、メソッド宣言から `this` 修飾子を削除します。  
  
## 使用例  
 次の例では、ファイルのコンパイルに System.Core.dll が含まれていない場合、CS1110 が生成されます。  
  
```  
// cs1110.cs // CS1110 // Compile with: /target:library public static class Extensions { public static bool Test(this bool b) { return b; } }  
```  
  
## 参照  
 [拡張メソッド](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)