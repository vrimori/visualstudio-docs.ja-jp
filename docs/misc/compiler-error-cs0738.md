---
title: "コンパイラ エラー CS0738 | Microsoft Docs"
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
  - "CS0738"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0738"
ms.assetid: 01ce94ee-2435-4326-befc-2b020c441a4f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0738
'type name' はインターフェイス メンバー 'member name' を実装しません。 'method name' は、一致する ' type name' の戻り値の型を持たないため、'interface member' を実装できません。  
  
 クラスの実装メソッドの戻り値は、実装するインターフェイス メンバーの戻り値と一致する必要があります。  
  
### このエラーを解決するには  
  
1.  インターフェイス メンバーの型と一致するように、メソッドの戻り値の型を変更します。  
  
## 使用例  
 クラス メソッドは `void` を返し、同じ名前のインターフェイス メンバーは `int` を返すため、次のコードでは、CS0738 が生成されます。  
  
```  
using System; interface ITest { int TestMethod(); } public class Test: ITest { public void TestMethod() { } // CS0738 // Try the following line instead. // public int TestMethod(); }  
```  
  
## 参照  
 [インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)