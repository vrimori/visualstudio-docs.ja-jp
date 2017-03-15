---
title: "コンパイラ エラー CS0276 | Microsoft Docs"
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
  - "CS0276"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0276"
ms.assetid: 0c49017f-c7a9-42a5-9d0a-6f1d82142bd7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0276
'property\/indexer': アクセサーのアクセシビリティ修飾子は、プロパティまたはインデクサーが get アクセサーおよび set アクセサーの両方を含む場合にのみ、使用されます。  
  
 このエラーは、1 つのアクセサーのみがあるプロパティまたはインデクサーを宣言して、アクセサーのアクセス修飾子を使用すると、発生します。 解決するには、アクセス修飾子を削除するか、別のアクセサーを追加します。  
  
## 使用例  
 次の例では、CS0276 が生成されます。  
  
```  
// CS0276.cs public class MyClass { public int Property { protected set { }   // CS0276 } public int Property2 { internal get { }   // CS0276 } }  
```