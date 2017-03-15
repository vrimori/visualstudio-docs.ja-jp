---
title: "コンパイラ エラー CS1917 | Microsoft Docs"
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
  - "CS1917"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1917"
ms.assetid: 05688706-e4b4-4273-9244-48cce1f7f9b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1917
型 'struct name' の読み取り専用フィールド 'name' のメンバーは、値の型であるため、オブジェクト初期化子と共に割り当てることはできません。  
  
 値の型である読み取り専用フィールドは、コンストラクターにのみ割り当てることができます。  
  
### このエラーを解決するには  
  
-   構造体をクラス型に変更します。  
  
-   コンストラクターを含む構造体を初期化します。  
  
## 使用例  
 次のコードでは CS1917 が生成されます。  
  
```  
// cs1917.cs class CS1917 { public struct TestStruct { public int i; } public class C { public readonly TestStruct str = new TestStruct(); public static int Main() { C c = new C { str = { i = 1 } }; // CS1917 return 0; } } }  
```