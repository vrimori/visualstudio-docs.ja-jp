---
title: "コンパイラ エラー CS1929 | Microsoft Docs"
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
  - "CS1929"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1929"
ms.assetid: effdd5d4-e156-418b-9d45-4ca194ab4319
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1929
インスタンス引数: 'typeA' から 'typeB' に変換できません。  
  
 このエラーは、拡張しないクラスから拡張メソッドを呼び出そうとすると生成されます。 次に示す例では、拡張メソッドは派生クラス `A` には定義されますが、基底クラス `B` には定義されません。  
  
### このエラーを解決するには  
  
1.  呼び出す必要のある型用の新しい拡張メソッドを作成するか、既存のメソッドを拡張する型のオブジェクトに呼び出しを移動します。  
  
## 使用例  
 次のコードでは CS1928 および CS1929 が生成されます。  
  
```  
// cs1929.cs using System.Linq; using System.Collections; static class Ext { public static void ExtMethod(this A a) { } } class A : B { } class B { static void Main() { B b = new B(); b.ExtMethod(); // CS1929 } }  
```  
  
## 参照  
 [拡張メソッド](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)