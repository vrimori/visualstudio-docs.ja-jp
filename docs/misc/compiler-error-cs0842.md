---
title: "コンパイラ エラー CS0842 | Microsoft Docs"
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
  - "CS0842"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0842"
ms.assetid: 93a8b333-efc4-40c7-ae53-5264f721a74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0842
自動的に実装されたプロパティは、StructLayout\(LayoutKind.Explicit\) でマークされた型の内部で使用できません。  
  
 自動実装プロパティにはコンパイラによって提供されるバッキング フィールドがあり、フィールドはソース コードにアクセスできません。 したがって、<xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> と互換性がありません。  
  
### このエラーを解決するには  
  
1.  プロパティをアクセサー本体が提供される通常のプロパティにします。  
  
## 使用例  
 次の例では、CS0842 が生成されます。  
  
```  
// cs0842.cs using System; using System.Runtime.InteropServices; namespace TestNamespace { [StructLayout(LayoutKind.Explicit)] struct Str { public int Num // CS0842 { get; set; } static int Main() { return 1; } } }  
```