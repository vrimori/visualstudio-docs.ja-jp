---
title: "コンパイラ エラー CS1509 | Microsoft Docs"
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
  - "CS1509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1509"
ms.assetid: 51a475c3-f085-49cb-89b0-c6582b68653f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1509
参照したファイル 'file' はアセンブリではありません。\/addmodule オプションを使用してください  
  
 [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) \(アセンブリ マニフェストを持たない\) を使用したコンパイルで生成された出力ファイル \(出力ファイル 1\) が、[\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) に対して指定されました。 そのため、現在のプログラムのアセンブリには、アセンブリが追加されずに、出力ファイル 1 に含まれるメタデータ情報が追加されます。