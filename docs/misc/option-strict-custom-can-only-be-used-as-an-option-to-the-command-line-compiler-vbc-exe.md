---
title: "Option Strict Custom はコマンドライン コンパイラ (vbc.exe) へのオプションとしてのみ使用することができます | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31141"
  - "bc31141"
helpviewer_keywords: 
  - "BC31141"
ms.assetid: c32ae8ff-aacc-40b4-960a-6f2d5d246671
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict Custom はコマンドライン コンパイラ (vbc.exe) へのオプションとしてのみ使用することができます
`Option Strict` ステートメントは、`On` と `Off` のみを引数として受け取ることができます。`Option Strict Custom` は使用できません。  
  
 厳密な言語セマンティクスが守られていないときに警告するには、`/optionstrict:custom` コンパイラ オプションを使用します。  
  
 **エラー ID:** BC31141  
  
### このエラーを解決するには  
  
1.  ソース コードから `Option Strict Custom` を削除します。  
  
2.  `/optionstrict:custom` オプションを指定します。 詳細については、「[\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)」を参照してください。  
  
## 参照  
 [Option \<keyword\> Statement](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)