---
title: "コンパイラ エラー CS1680 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1680"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1680"
ms.assetid: 973da155-e6fa-4de8-94fd-7838f839a81f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1680
無効な参照エイリアス オプションです: 'alias\=' \-\- ファイル名が指定されていません。  
  
 このエラーは、有効なファイル名を指定せずに、**\/reference** コンパイラ オプションを指定して `alias` 機能を使用した場合に発生します。  
  
 次の例では CS1680 が生成されます。  
  
```  
// CS1680.cs // compile with: /reference:alias= // CS1680 expected // To resolve, specify the name of a file with an assembly manifest class MyClass {}  
  
```