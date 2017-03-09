---
title: "コンパイラ エラー CS0526 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0526"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0526"
ms.assetid: befc46b4-28ea-40d3-89ac-132b92455772
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0526
インターフェイスにコンストラクターを含めることはできません。  
  
 [インターフェイス](/dotnet/csharp/language-reference/keywords/interface)にコンストラクターを定義することはできません。 クラスと同じ名前で戻り値の型がないメソッドは、コンストラクターと見なされます。  
  
 次の例では CS0526 が生成されます。  
  
```  
// CS0526.cs namespace x { public interface clx { public clx()   // CS0526 { } } public class cly { public static void Main() { } } }  
```