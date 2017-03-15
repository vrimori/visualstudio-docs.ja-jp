---
title: "コンパイラ エラー CS0041 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0041
'type' の完全修飾名がデバッグ情報に対して長すぎます '\/debug' オプションなしでコンパイルします。  
  
 このエラーは、[\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) コンパイラ オプションを使用すると発生することがあります。 このエラーが発生した場合は、bin ディレクトリ内の PDB ファイルを削除してから再コンパイルしてみてください。 引き続きこのエラーが発生する場合は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の修復または再インストールが必要になることがあります。