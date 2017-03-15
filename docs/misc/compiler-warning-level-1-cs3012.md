---
title: "コンパイラの警告 (レベル 1) CS3012 | Microsoft Docs"
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
  - "CS3012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3012"
ms.assetid: 1f7555b4-61e4-4821-85c9-586301df4c5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3012
アセンブリの CLSCompliant 属性と異なるモジュールの CLSCompliant 属性は指定できません  
  
 `[module:System.CLCSompliant(true)]` を通じて、モジュールが共通言語仕様 \(CLS\) に準拠するためには、[\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) コンパイラ オプションを使用してビルドする必要があります。 CLS の詳細については、「[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)」を参照してください。  
  
## 使用例  
 次の例では、`/target:module` を使用せずにビルドすると CS3012 が生成されます。  
  
```  
// CS3012.cs // compile with: /W:1 [module:System.CLSCompliant(true)]   // CS3012 public class C { public static void Main() { } }  
```