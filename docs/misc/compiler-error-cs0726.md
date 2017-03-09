---
title: "コンパイラ エラー CS0726 | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0726
'format specifier' は有効な形式指定子ではありません  
  
 このエラーは、デバッガーで発生します。 デバッガー ウィンドウのいずれかに変数名を入力すると、コンマ、その次に書式指定子を指定して追跡できます。 たとえば、「`myInt, h`」や「`myString,nq`」のようになります。 このエラーは、コンパイラが [C\# の書式指定子](../debugger/format-specifiers-in-csharp.md) を認識しない場合に発生します。