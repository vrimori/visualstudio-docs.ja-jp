---
title: "コンパイラ エラー CS0573 | Microsoft Docs"
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
  - "CS0573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0573"
ms.assetid: 10ef9625-44f1-4936-ada3-56938357aa01
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0573
'field declaration': 構造体にインスタンス フィールド初期化子を指定することはできません  
  
 [構造体](/dotnet/csharp/language-reference/keywords/struct) のインスタンス フィールドを初期化することはできません。 値型のフィールドは既定値に初期化され、参照型のフィールドは `null` に初期化されます。  
  
## 使用例  
 次の例では CS0573 が生成されます。  
  
```  
// CS0573.cs namespace x { public class clx { public static void Main() { } } public struct cly { clx a = new clx();   // CS0573 // clx a;            // OK int i = 7;           // CS0573 // int i;            // OK } }  
```