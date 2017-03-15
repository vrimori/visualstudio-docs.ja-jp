---
title: "コンパイラ エラー CS0274 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0274"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0274"
ms.assetid: bbd2d64e-a756-4713-b9ed-711d50b65e00
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0274
プロパティまたはインデクサー 'property\/indexer' の両方のアクセサーにアクセシビリティ修飾子を指定することはできません。  
  
 このエラーは、両方のアクセサーに対するアクセス修飾子を持つプロパティまたはインデクサーを宣言するときに発生します。 このエラーを解決するには、2 つのアクセサーのうちどちらかのアクセス修飾子のみを使用します。 詳細については、「[アクセサーのアクセシビリティ](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility)」を参照してください。  
  
 次の例では、CS0274 が生成されます。  
  
```  
// CS0274.cs public class MyClass { public int Property   // CS0274 { public get { return 0; } protected set { } } }  
```