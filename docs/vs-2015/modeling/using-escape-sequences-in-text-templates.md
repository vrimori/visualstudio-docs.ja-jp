---
title: テキスト テンプレートでエスケープ シーケンスの使用 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 24e2629001d7c426193059175eab64ea0ab8dacf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537763"
---
# <a name="using-escape-sequences-in-text-templates"></a>テキスト テンプレートでのエスケープ シーケンスの使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[テキスト テンプレートでエスケープ シーケンスを使用して](https://docs.microsoft.com/visualstudio/modeling/using-escape-sequences-in-text-templates)します。  
  
エスケープ シーケンスを使用するには、テキスト テンプレートのタグを生成するテキスト テンプレートでは (c# コードのみ) でエスケープ制御文字や引用符にします。  
  
 出力ファイルに標準のコード ブロックの始めと終わりのタグを印刷するには、次のように、タグをエスケープします。  
  
```  
\<# ... \#>  
```  
  
 その他のテキスト テンプレート ディレクティブとコード ブロック タグと同じの操作を行うことができます。  
  
 テキスト ブロックには、テキスト テンプレートのタグをエスケープするために使用する文字列が含まれている場合は、次のエスケープ シーケンスを使用することがあります。  
  
-   テキスト テンプレートのタグの偶数のエスケープが付きます (\\) 文字をテンプレート パーサーがエスケープ文字の半分を含めるし、テキスト テンプレートのタグとしてシーケンスが含まれます。 たとえば、テキスト テンプレートに 4 つのエスケープ文字がある場合があります 2"\\"生成されたファイル内の文字。  
  
-   テキスト テンプレートのタグのエスケープの数が奇数が付きます (\\) 文字、テンプレート パーサーが含まれますの半分、"\\"文字と、タグ自体 (\<# または #>)。 タグは、テキスト テンプレートのタグであると見なされません。  
  
-   場合、エスケープ (\\) 文字では、制御文字または引用符 (c# のみ) をエスケープ以外の任意の順序で他の場所が表示されたら、文字が直接出力されます。  
  
## <a name="see-also"></a>関連項目  
 [方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)



