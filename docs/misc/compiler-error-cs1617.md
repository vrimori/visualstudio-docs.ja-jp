---
title: "コンパイラ エラー CS1617 | Microsoft Docs"
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
  - "CS1617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1617"
ms.assetid: fd3371ed-39eb-4d3d-b8f5-d96ac0c79398
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1617
\/langversion に対するオプション 'option' は無効です。ISO\-1、ISO\-2、または Default を指定してください  
  
 このエラーは、[\/langversion](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option) コマンド ライン スイッチまたはプロジェクト設定を使用し、有効な言語オプションを指定しなかった場合に発生します。 このエラーを解決するには、コマンド ライン構文またはプロジェクト設定を確認し、表示されたオプションのいずれかに変更します。  
  
 たとえば、`csc /langversion:ISO` でコンパイルすると、エラー CS1617 が生成されます。