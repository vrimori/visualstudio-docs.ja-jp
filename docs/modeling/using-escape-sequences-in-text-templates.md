---
title: テキスト テンプレートでのエスケープ シーケンスの使用
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b8e92a4bbd149d96b6db710daf32dc72024d57da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950388"
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

- [方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)