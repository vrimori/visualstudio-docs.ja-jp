---
title: "空の文字セットが指定されました。 | Microsoft Docs"
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
  - "vs.message.VS_E_RE_EMPTYSET"
  - "vs.message.0x800A00DF"
ms.assetid: 27ed2ebe-a492-4bc9-ab33-a09fba6cf1d3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 空の文字セットが指定されました。
通常、このエラーが発生するのは、\[正規表現\] がオンになっていて、文字セット \[\] または \[^\] のパターンに不完全な構文を含む文字列を指定した場合です。  たとえば、`[}` のようにします。  
  
### このエラーを解決するには  
  
1.  「正規表現」のトピックを参照して正しいパターン構文を検討し、文字列を再入力します。  
  
## 参照  
 [Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/ja-jp/dad03582-4931-4893-83ba-84b37f5b1600)   
 [\[フォルダーを指定して検索\]](../ide/find-in-files.md)   
 [テキストの検索と置換](../ide/finding-and-replacing-text.md)