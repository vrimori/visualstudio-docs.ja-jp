---
title: "Argument is missing in &#39;\&#39; escape sequence. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_ESCAPEMISSINGARG"
  - "vs.message.0x800A00BD"
ms.assetid: 5bd6559b-8cd9-450f-91c8-335ff1b1ef86
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Argument is missing in &#39;\&#39; escape sequence.
このエラーは一般的に、検索文字列に正規表現またはワイルドカードを使用した場合の検索または置換で発生します。  このエラーは、パターンの末尾に単一の円記号 \(`\`\) がある場合や、有効な 16 進 Unicode 文字を伴わずに「`\x`」または「`\u`」を入力した場合に発生します。  
  
### このエラーを解決するには  
  
1.  正規表現のエスケープ文字を使用して検索するには、「`\`」を入力します。  
  
2.  Unicode 文字を検索するには、「`\x`」または「`\u`」を入力した後に有効な Unicode 値を入力します。  
  
3.  リテラル円記号を検索するには、「`\\`」を使用します。  
  
## 参照  
 [Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/ja-jp/dad03582-4931-4893-83ba-84b37f5b1600)   
 [\[フォルダーを指定して検索\]](../ide/find-in-files.md)