---
title: "コンパイラ エラー CS1024 | Microsoft Docs"
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
  - "CS1024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1024"
ms.assetid: 41f587cb-1958-4eb6-9f8d-c03500e55e21
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1024
プリプロセッサ ディレクティブが必要です。  
  
 行の先頭はシャープ記号 \(\#\) ですが、後続の文字列が有効な[プリプロセッサ ディレクティブ](/dotnet/csharp/language-reference/preprocessor-directives/index)ではありませんでした。  
  
 次の例では CS1024 が生成されます。  
  
```  
// CS1024.cs #import System   // CS1024  
```