---
title: "テキスト テンプレートでエスケープ シーケンスの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fdf062c9b33dd4a160f54bba83991a3cdda7f0d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="using-escape-sequences-in-text-templates"></a>テキスト テンプレートでのエスケープ シーケンスの使用
エスケープ シーケンスを使用するには、テキスト テンプレートのタグを生成するテキスト テンプレートでは (c# コードのみ) でエスケープ制御文字や引用符をします。  
  
 出力ファイルに標準のコード ブロックの始めと終わりのタグを印刷するには、次のようにタグをエスケープします。  
  
```  
\<# ... \#>  
```  
  
 その他のテキスト テンプレート ディレクティブおよびコード ブロック タグと同じを行うことができます。  
  
 テキスト ブロックには、テキスト テンプレート タグをエスケープするために使用される文字列が含まれている場合は、次のエスケープ シーケンスを使用することがあります。  
  
-   テキスト テンプレートのタグはエスケープの偶数を付けたかどうか (\\) 文字が、テンプレート パーサーはそのエスケープ文字の半分とテキスト テンプレート タグとして文字列が含まれています。 たとえば、テキスト テンプレートに次の 4 つのエスケープ文字がある場合がある 2 つの"\\"生成されたファイル内の文字です。  
  
-   テキスト テンプレートのタグはエスケープの数が奇数に続くかどうか (\\) 文字、テンプレート パーサーが含まれますの半分、"\\"文字、タグ自体と (\<# または #>)。 タグは、テキスト テンプレート タグではありません。  
  
-   場合、エスケープ (\\) 文字では、制御文字または引用符 (C# の場合のみ) をエスケープ以外の任意の順序で他の場所が表示されたら、文字が直接出力します。  
  
## <a name="see-also"></a>関連項目  
 [方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)