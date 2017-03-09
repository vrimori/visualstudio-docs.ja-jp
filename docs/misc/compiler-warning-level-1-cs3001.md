---
title: "コンパイラの警告 (レベル 1) CS3001 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3001"
ms.assetid: c4f3e247-5e47-4182-b415-c573fb1a152f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3001
引数型 'type' は CLS に準拠していません  
  
 [public](/dotnet/csharp/language-reference/keywords/public)、[protected](/dotnet/csharp/language-reference/keywords/protected)、または `protected` `internal` メソッドは、共通言語仕様 \(CLS\) に準拠した型を持つパラメーターを受け入れる必要があります。 CLS 準拠の詳細については、「[CLS準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)」および「[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)」を参照してください。  
  
## 使用例  
 次の例では、CS3001 エラーが生成されます。  
  
```  
// CS3001.cs [assembly:System.CLSCompliant(true)] public class a { public void bad(ushort i)   // CS3001 { } private void OK(ushort i)   // OK, private method { } public static void Main() { } }  
```