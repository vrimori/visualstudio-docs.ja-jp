---
title: "コンパイラの警告 (レベル 1) CS3017 | Microsoft Docs"
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
  - "CS3017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3017"
ms.assetid: 8e56b2f0-9caf-4c9a-98c2-d3ad0b70e767
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3017
アセンブリの CLSCompliant 属性と異なるモジュールの CLSCompliant 属性は指定できません  
  
 モジュールの CLSCompliant 属性と矛盾するアセンブリの CLSCompliant 属性があると、この警告が発生します。 CLS 準拠であるアセンブリには、CLS 準拠でないモジュールを含めることができません。 この警告を解決するには、アセンブリとモジュールの CLSCompliant 属性を両方 true、または両方 false のどちらかにするか、片方の属性を削除してください。 CLS 準拠について詳しくは、「[CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)」および「[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)」をご覧ください。  
  
## 使用例  
 次の例では、CS3017 が生成されます。  
  
```  
// CS3017.cs // compile with: /target:module using System; [module: CLSCompliant(true)] [assembly: CLSCompliant(false)]  // CS3017 // Try this line instead: // [assembly: CLSCompliant(true)] class C { static void Main() {} }  
```