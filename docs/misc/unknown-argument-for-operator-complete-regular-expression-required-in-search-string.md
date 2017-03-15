---
title: "Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string. | Microsoft Docs"
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
  - "vs.message.0x800A00BE"
  - "vs.message.VS_E_RE_SPECIALUNKNOWN"
ms.assetid: 8cbc2f7f-7ea1-4803-904c-1f716cd36376
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string.
このエラーは一般的に、検索文字列に正規表現またはワイルドカードを使用した場合の検索または置換で発生します。  コロン演算子 \(`:`\) が入力された後の引数が有効な引数ではありません。  
  
> [!NOTE]
>  コロン \(`:`\) 演算子の引数は、大文字と小文字を区別します。  
  
### このエラーを解決するには  
  
1.  「正規表現」に示した正規表現の正しい構文を再確認します。  
  
2.  引数に使用した大文字小文字が正しいことを入念にチェックします。  
  
3.  IME \(Input Method Editor\) を使用する場合は、引数に全角文字が使用されていないことを確認します。  
  
## 参照  
 [Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/ja-jp/dad03582-4931-4893-83ba-84b37f5b1600)   
 [\[フォルダーを指定して検索\]](../ide/find-in-files.md)