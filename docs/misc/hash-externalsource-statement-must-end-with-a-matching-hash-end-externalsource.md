---
title: "&#39;#ExternalSource&#39; ステートメントの終わりには、対応する &#39;#End ExternalSource&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30579"
  - "bc30579"
helpviewer_keywords: 
  - "BC30579"
ms.assetid: 8d658008-eddc-4b7d-a8d4-036da42957bf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ExternalSource&#39; ステートメントの終わりには、対応する &#39;#End ExternalSource&#39; を指定しなければなりません
`#ExternalSource` ディレクティブは外部のコードを参照して、そのコード内でいつ例外が発生したのかをコンパイラが正確に報告できるようにしています。`#ExternalSource` ブロックは `#ExternalSource` で始まり、`#End ExternalSource` で終わる必要があります。  
  
 **エラー ID:** BC30579  
  
### このエラーを解決するには  
  
1.  `#End ExternalSource` をコード内の適切な場所に追加します。  
  
2.  不要な場合には、最初の `#ExternalSource` を削除します。  
  
## 参照  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD 条件付きコンパイル \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)