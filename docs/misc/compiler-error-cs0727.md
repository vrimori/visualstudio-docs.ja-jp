---
title: "コンパイラ エラー CS0727 | Microsoft Docs"
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
  - "CS0727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0727"
ms.assetid: 54bfb87e-d759-4310-a8ab-02dccd06337c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0727
無効な形式指定子です。  
  
 このエラーは、デバッガーで発生します。 デバッガー ウィンドウのいずれかに変数名を入力するときに、変数名に続けて、コンマおよび書式指定子を入力できます。 たとえば、myInt, h や myString,nq のように入力できます。 このエラーは、入力した内容をコンパイラが完全に解析できなかった場合に発生します。 このエラーを解決するには、変数名と、任意でコンマおよび[有効な書式指定子](../debugger/format-specifiers-in-csharp.md)を再度入力します。