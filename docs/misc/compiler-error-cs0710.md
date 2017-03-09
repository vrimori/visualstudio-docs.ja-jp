---
title: "コンパイラ エラー CS0710 | Microsoft Docs"
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
  - "CS0710"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0710"
ms.assetid: 753a1a87-f5e5-4758-a960-515069a6c7b0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0710
静的クラスにはコンストラクターを指定できません。  
  
 静的クラスはインスタンス化できないため、コンストラクターは必要ありません。 このエラーを回避するには、静的クラスからコンストラクターを削除します。または、実際にインスタンスを構築する必要がある場合は、クラスを非静的にします。  
  
 次の例では CS0710 が生成されます。  
  
```  
// CS0710.cs public static class C { public C()  // CS0710 { } public static void Main() { } }  
```