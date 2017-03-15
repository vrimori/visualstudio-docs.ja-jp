---
title: "コンパイラの警告 (レベル 2) CS3019 | Microsoft Docs"
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
  - "CS3019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3019"
ms.assetid: b41117cf-8956-4989-93fd-9903812e2d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS3019
'type' はこのアセンブリの外から認識できないため、'type' で CLS 準拠の確認は実行されません  
  
 この警告は、<xref:System.CLSCompliantAttribute> 属性を持つ型またはメンバーが別のアセンブリからは見えない場合に発生します。 このエラーを解決するには、他のアセンブリから見えないクラスまたはメンバーの属性を削除するか、型またはメンバーが見えるようにします。 CLS 準拠の詳細については、「[\<PAVE OVER\> CLS準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)」を参照してください。  
  
## 使用例  
 次の例では CS3019 が生成されます。  
  
```  
// CS3019.cs // compile with: /W:2 using System; [assembly: CLSCompliant(true)] // To fix the error, remove the next line [CLSCompliant(true)]  // CS3019 class C { [CLSCompliant(false)]  // CS3019 void Foo() { } static void Main() { } }  
```  
  
## 参照  
 [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)