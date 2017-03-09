---
title: "コンパイラ エラー CS1609 | Microsoft Docs"
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
  - "CS1609"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1609"
ms.assetid: 89e112f8-6337-4803-8741-2e38497deb8c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1609
修飾子をイベント アクセサー宣言に付属させることはできません。  
  
 修飾子はイベント宣言にのみ付属でき、イベント アクセサー宣言には付属させることはできません。 詳細については、「[プロパティの使用](/dotnet/csharp/programming-guide/classes-and-structs/using-properties)」を参照してください。  
  
## 使用例  
 次の例では CS1609 が生成されます。  
  
```  
// CS1609.cs // compile with: /target:library delegate int Del(); class A { public event Del MyEvent { private add {}   // CS1609 // try the following line instead // add {} remove {} } }  
```