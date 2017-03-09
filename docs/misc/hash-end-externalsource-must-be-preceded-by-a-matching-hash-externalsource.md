---
title: "&#39;#End ExternalSource&#39; の前には、対応する &#39;#ExternalSource&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30578"
  - "vbc30578"
helpviewer_keywords: 
  - "BC30578"
ms.assetid: f011673d-eced-46a7-a08e-d54d86c8a76b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End ExternalSource&#39; の前には、対応する &#39;#ExternalSource&#39; を指定しなければなりません
`#ExternalSource` ディレクティブは、外部のコードを参照しており、そのコード内でいつ例外が発生したのかをコンパイラが正確に報告できるようにします。`#ExternalSource` ブロックは `#ExternalSource` で始まり、`#End ExternalSource` で終わる必要があります。  
  
 **エラー ID:** BC30578  
  
### このエラーを解決するには  
  
1.  `#ExternalSource` をコード内の適切な場所に追加します。  
  
2.  不要な場合は、`#End ExternalSource` を削除します。  
  
## 参照  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [ビルド内にありません: 条件付きコンパイル \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)