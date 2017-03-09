---
title: "コンパイラ エラー CS0522 | Microsoft Docs"
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
  - "CS0522"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0522"
ms.assetid: f749f21e-92ee-495c-9b53-179ce9342d05
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0522
'constructor': 構造体は基底クラスのコンストラクターを呼び出すことができません  
  
 [構造体](/dotnet/csharp/language-reference/keywords/struct)は基底クラスのコンストラクターを呼び出すことはできません。基底クラスのコンストラクターの呼び出しを削除します。  
  
 次の例では CS0522 が生成されます。  
  
```  
// CS0522.cs public class clx { public clx(int i) { } public static void Main() { } } public struct cly { public cly(int i):base(0)   // CS0522 // try the following line instead // public cly(int i) { } }  
```