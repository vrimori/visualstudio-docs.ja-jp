---
title: "コンパイラ エラー CS1551 | Microsoft Docs"
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
  - "CS1551"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1551"
ms.assetid: 09fde2a2-7466-418a-88ef-395321358b07
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1551
インデクサーには最低パラメーターが 1 つ必要です。  
  
 引数を受け取らない[インデクサー](/dotnet/csharp/programming-guide/indexers/index)が宣言されました。  
  
 次の例では CS1551 が生成されます。  
  
```  
// CS1551.cs public class MyClass { int intI; int this[]   // CS1551 // try the following line instead // int this[int i] { get { return intI; } set { intI = value; } } public static void Main() { } }  
```