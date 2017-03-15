---
title: "整数の定数が必要です | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30204"
  - "vbc30204"
helpviewer_keywords: 
  - "BC30204"
ms.assetid: e8d2fe24-7e63-4c30-b022-3b0323f00f4e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 整数の定数が必要です
2 番目の引数が整数リテラルでない `#ExternalSource` ディレクティブがあります。 このコンテキストでは、整数リテラルだけが有効です。 名前付き定数または列挙型のメンバーは無効です。  
  
 **エラー ID:** BC30204  
  
### このエラーを解決するには  
  
1.  リテラルの代わりに、名前付き定数か列挙体のメンバーを使用します。  
  
2.  `#ExternalSource` ディレクティブの 2 番目の引数として整数リテラルを指定します。  
  
## 参照  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)