---
title: "コンパイラ エラー CS1025 | Microsoft Docs"
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
  - "CS1025"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1025"
ms.assetid: 491c186f-cb40-47a9-9656-44fadfa18ae2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1025
単一行コメントか行の終わりが必要です。  
  
 [プリプロセッサ ディレクティブ](/dotnet/csharp/language-reference/preprocessor-directives/index) がある行に複数行のコメントを記述することはできません。  
  
 次の例では CS1025 が生成されます。  
  
```  
#if true /* hello */   // CS1025 #endif   // this is a good comment  
```  
  
 CS1025 は、次のように、一部の無効なプリプロセッサ ディレクティブを試行した場合にも発生することがあります。  
  
```  
// CS1025.cs #define a class Sample { static void Main() { #if a 1   // CS1025, invalid syntax System.Console.WriteLine("Hello, World!"); #endif } }  
```