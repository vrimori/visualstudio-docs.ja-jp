---
title: "コンパイラ エラー CS0689 | Microsoft Docs"
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
  - "CS0689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0689"
ms.assetid: 5c555c2e-8e71-4097-8dbf-52dbafe7bf57
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0689
'identifier' は型パラメーターであるため、派生させることはできません。  
  
 ジェネリック クラスの基底クラスまたはインターフェイスは、型パラメーターでは指定できません。 代わりに、特定のクラスかインターフェイス、または特定のジェネリック クラスから派生するか、不明な型をメンバーとして含めるようにします。  
  
 次の例では CS0689 が生成されます。  
  
```  
// CS0689.cs class A<T> : T   // CS0689 { }  
```