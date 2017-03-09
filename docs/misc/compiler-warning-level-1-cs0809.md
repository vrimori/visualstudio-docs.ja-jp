---
title: "コンパイラの警告 (レベル 1) CS0809 | Microsoft Docs"
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
  - "CS0809"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0809"
ms.assetid: 2c2f0248-ab3a-4cdc-a1b0-2f0e05eac4c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0809
旧形式のメンバー 'memberA' が、旧形式でないメンバー 'memberB' をオーバーライドします。  
  
 通常、不使用とマークされているメンバーで不使用とマークされていないメンバーをオーバーライドしないでください。 この警告は [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] で生成されますが、[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] では生成されません。  
  
### このエラーを解決するには  
  
1.  `Obsolete` 属性を、オーバーライドするメンバーから削除するか、または基底クラスのメンバーに追加します。  
  
## 使用例  
  
```  
// CS0809.cs public class Base { public virtual void Test1() { } } public class C : Base { [System.Obsolete()] public override void Test1() // CS0809 { } }  
```