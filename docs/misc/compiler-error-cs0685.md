---
title: "コンパイラ エラー CS0685 | Microsoft Docs"
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
  - "CS0685"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0685"
ms.assetid: 20d7c6cf-a388-430f-b22b-232536912491
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0685
条件付きメンバー 'member' には out パラメーターを指定できません  
  
 メソッドで <xref:System.Diagnostics.ConditionalAttribute> 属性を使用する場合、そのメソッドに out パラメーターがない可能性があります。 これは、メソッド呼び出しが nothing にコンパイルされる場合、out パラメーターに使用される変数の値が定義されないためです。 このエラーを避けるためには、条件付きのメソッド宣言から out パラメーターを削除するか、条件付きの属性を使用しないでください。  
  
## 使用例  
 次の例では CS0685 が生成されます。  
  
```  
// CS0685.cs using System.Diagnostics; class C { [Conditional("DEBUG")] void trace(out int i)  // CS0685 { i = 1; } }  
```