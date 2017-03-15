---
title: "コンパイラの警告 (レベル 1) CS1696 | Microsoft Docs"
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
  - "CS1696"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1696"
ms.assetid: 69a45988-1aba-4a01-a84e-7ca59f8dde28
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1696
単一行コメントか行の終わりが必要です。  
  
 コンパイラでは、プリプロセッサ ディレクティブの後に、行末の終端記号または単一行コメントが必要です。 コンパイラにより、有効なプリプロセッサ ディレクティブの処理が終了しましたが、この構文制約に対する何らかの違反が検出されました。  
  
## 使用例  
 次の例では CS1696 が生成されます。  
  
```  
// CS1696.cs class Test { public static void Main() { #pragma warning disable 1030;219   // CS1696 #pragma warning disable 1030   // OK } }  
```