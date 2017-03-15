---
title: "コンパイラ エラー CS0273 | Microsoft Docs"
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
  - "CS0273"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0273"
ms.assetid: 851ad056-feee-48fd-834c-578a1a13e926
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0273
'property\_accessor' アクセサーのアクセシビリティ修飾子は、プロパティまたはインデクサー 'property' よりも制限されていなければなりません  
  
 set\/get アクセサーのアクセシビリティ修飾子は、プロパティまたはインデクサー 'property\/indexer' よりも制限されていなければなりません  
  
 このエラーは、プロパティまたはインデクサーに対して、それらのアクセサーよりも制限の厳しいアクセス修飾子が宣言されている場合に発生します。 このエラーを解決するには、プロパティまたは set アクセサーに適切なアクセス修飾子を使用します。 詳細については、「[アクセサーのアクセシビリティ](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility)」を参照してください。  
  
## 使用例  
 この例には、内部 set メソッドを持つ内部プロパティが含まれています。 次の例では CS0273 が生成されます。  
  
```  
// CS0273.cs // compile with: /target:library public class MyClass { internal int Property { get { return 0; } internal set {}   // CS0273 // try the following line instead // private set {} } }  
```