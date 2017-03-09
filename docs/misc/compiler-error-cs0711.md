---
title: "コンパイラ エラー CS0711 | Microsoft Docs"
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
  - "CS0711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0711"
ms.assetid: 3a5a6d90-e15d-4808-a7a6-c85fd011a0d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0711
静的クラスにデストラクターを含めることはできません。  
  
 静的クラスはインスタンス化できないため、コンストラクターまたはデストラクターは必要ありません。 このエラーを回避するには、静的クラスからデストラクターを削除します。または、実際にインスタンスを構築または破棄する必要がある場合は、クラスを非静的にします。  
  
 次の例では CS0711 が生成されます。  
  
```  
// CS0711.cs public static class C { ~C()  // CS0711 { } public static void Main() { } }  
```