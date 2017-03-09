---
title: "コンパイラ エラー CS0677 | Microsoft Docs"
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
  - "CS0677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0677"
ms.assetid: 6a4a3703-9b44-4c4f-a564-8b437b1cb6b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0677
'variable': volatile フィールドの型を 'type' にすることはできません  
  
 `volatile` キーワードを使用して宣言されたフィールドは、次のいずれかの型である必要があります。  
  
-   すべての参照型  
  
-   すべてのポインター型 \(`unsafe` コンテキストの場合\)  
  
-   型 `sbyte`、**byte**、**short**、`ushort`、`int`、`uint`、`char`、**float**、`bool`  
  
-   上記のいずれかの型に基づく列挙型  
  
 次の例では CS0677 が生成されます。  
  
```  
// CS0677.cs class TestClass { private volatile long i;   // CS0677 public static void Main() { } }  
```