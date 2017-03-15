---
title: "コンパイラ エラー CS0636 | Microsoft Docs"
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
  - "CS0636"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0636"
ms.assetid: 47597f89-fbe6-4708-9493-3c86c6f0ce56
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0636
FieldOffset 属性は、StructLayout\(LayoutKind.Explicit\) でマークされた型のメンバーでのみ使用できます  
  
 **FieldOffset** 属性でマークされたメンバーが含まれている場合は、構造体の宣言で、**StructLayout\(LayoutKind.Explicit\)** 属性を使用する必要があります。 詳細については、「[FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic)」を参照してください。  
  
 次の例では CS0636 が生成されます。  
  
```  
// CS0636.cs using System; using System.Runtime.InteropServices; // To resolve the error, uncomment the following line: // [StructLayout(LayoutKind.Explicit)] struct Worksheet { [FieldOffset(4)]public int i;   // CS0636 } public class MainClass { public static void Main () { } }  
```