---
title: "&#39;#ExternalSource&#39; ディレクティブは入れ子にできません | Microsoft Docs"
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
  - "bc30580"
  - "vbc30580"
helpviewer_keywords: 
  - "BC30580"
ms.assetid: 56c6ef4b-28b1-4a62-8afa-d83a7742b507
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ExternalSource&#39; ディレクティブは入れ子にできません
`#ExternalSource` ディレクティブを別の `#ExternalSource` ブロック内に配置しようとしました。`#ExternalSource` ディレクティブは外部のコードを参照して、そのコード内でいつ例外が発生したのかをコンパイラが正確に報告できるようにしています。  
  
 `#ExternalSource` ブロックを別の `#ExternalSource` ブロック内に入れ子にすることはできません。  
  
 **エラー ID:** BC30580  
  
### このエラーを解決するには  
  
-   内側の `#ExternalSource` ディレクティブを、囲んでいる `#ExternalSource` ブロックの外に移動します。  
  
## 参照  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD 条件付きコンパイル \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)