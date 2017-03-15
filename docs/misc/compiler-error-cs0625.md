---
title: "コンパイラ エラー CS0625 | Microsoft Docs"
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
  - "CS0625"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0625"
ms.assetid: 44091813-9988-436c-b35e-e24094793782
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0625
'field': StructLayout\(LayoutKind.Explicit\) でマークされたインスタンス フィールドの型には、FieldOffset 属性を指定する必要があります  
  
 構造体が明示的な **StructLayout** 属性でマークされている場合、その構造体のすべてのフィールドには [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic) 属性が必要です。 詳細については、「[StructLayoutAttribute クラス](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic)」を参照してください。  
  
 次の例では CS0625 が生成されます。  
  
```  
// CS0625.cs // compile with: /target:library using System; using System.Runtime.InteropServices; [StructLayout(LayoutKind.Explicit)] struct A { public int i;   // CS0625 not static; an instance field } // OK [StructLayout(LayoutKind.Explicit)] struct B { [FieldOffset(5)] public int i; }  
```