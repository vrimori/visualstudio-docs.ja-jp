---
title: "コンパイラ エラー CS0644 | Microsoft Docs"
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
  - "CS0644"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0644"
ms.assetid: 835f3ee2-f897-4ba2-ad13-af629a9ab7fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0644
'class1' は特殊クラス 'class2' から派生することはできません  
  
 次に示す基底クラスから、クラスを明示的に継承することはできません。  
  
-   **System.Enum**  
  
-   **System.ValueType**  
  
-   **System.Delegate**  
  
-   **System.Array**  
  
 これらはコンパイラによって、暗黙的な基底クラスとして使用されます。 たとえば、**System.ValueType** は構造体の暗黙的な基底クラスです。  
  
 次の例では CS0644 が生成されます。  
  
```  
// CS0644.cs class MyClass : System.ValueType   // CS0644 { }  
```