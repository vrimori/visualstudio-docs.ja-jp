---
title: "コンパイラ エラー CS1667 | Microsoft Docs"
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
  - "CS1667"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1667"
ms.assetid: 59f64828-58bc-487c-862a-75537e21d4ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1667
属性 'attribute' は、プロパティまたはイベント アクセサーでは使用できません。 'declaration type' の宣言のみに使用できます。  
  
 このエラーは、ある属性がイベントまたはアクセサー上で使用されると同時に、そのプロパティまたはイベント自体に存在する必要がある場合に発生します。 このエラーは、属性 <xref:System.CLSCompliantAttribute>、<xref:System.Diagnostics.ConditionalAttribute>、および <xref:System.ObsoleteAttribute> で発生することがあります。  
  
## 使用例  
 次の例では CS1670 が生成されます。  
  
```  
// CS1667.cs using System; public class C { private int i; //Try this instead: //[Obsolete] public int ObsoleteProperty { [Obsolete]  // CS1667 get { return i; } set { i = value; } } public static void Main() { } }  
```