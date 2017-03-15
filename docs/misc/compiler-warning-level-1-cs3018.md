---
title: "コンパイラの警告 (レベル 1) CS3018 | Microsoft Docs"
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
  - "CS3018"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3018"
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3018
CLS に準拠していない型 'type' のメンバーであるため、'type' を CLS 準拠として設定できません  
  
 この警告は、CLSCompliant 属性が `true` に設定された入れ子のクラスが、CLSCompliant 属性が `false` に設定されたクラスのメンバーとして宣言されている場合に発生します。 CLS 準拠ではない外部クラスのメンバーである場合、入れ子になったクラスを CLS 準拠にすることはできないため、このような記述は使用できません。 この警告を解決するには、入れ子になったクラスから CLSCompliant 属性を削除するか、属性の設定を `true` から `false` に変更します。 CLS 準拠の詳細については、「[CLS準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)」および「[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)」を参照してください。  
  
## 使用例  
 次の例では CS3018 が生成されます。  
  
```  
// CS3018.cs // compile with: /target:library using System; [assembly: CLSCompliant(true)] [CLSCompliant(false)] public class Outer { [CLSCompliant(true)]   // CS3018 public class Nested {} // OK public class Nested2 {} [CLSCompliant(false)] public class Nested3 {} }  
```