---
title: "コンパイラ エラー CS1541 | Microsoft Docs"
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
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1541
無効な参照オプション: 'symbol' \-\- ディレクトリを参照できません  
  
 特定のファイルではなくディレクトリの指定がコンパイラによって検出されました。 たとえば、[\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) コンパイラ オプションを使用する場合は、ファイルを指定する必要があります。ディレクトリは指定できません。  
  
 たとえば、コンパイラに `/reference:c:\` を渡すと、CS1541 エラーが生成されます。