---
title: 'チュートリアル : XSLT スタイル シートのデバッグ'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebc8e8f8700690a2ae74fcc91384fb77b238ea33
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693397"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>チュートリアル: XSLT スタイル シートをデバッグします。

このチュートリアルの手順では、XSLT デバッガーを使用する方法を示します。 変数の表示、ブレークポイントの設定、コードのステップ実行などの手順が含まれます。 このスタイル シートでは、平均書籍価格を下回るすべての書籍が検索されます。

## <a name="to-prepare-for-this-walkthrough"></a>このチュートリアルの準備をするには

1.  開かれているソリューションをすべて閉じます。

2.  2 つのサンプル ファイルをローカル コンピューターにコピーします。

## <a name="start-debugging"></a>[デバッグ開始]

### <a name="to-start-debugging"></a>デバッグを開始するには

1.  **ファイル** メニューのをポイント**開く**、 をクリック**ファイル**です。

2.  検索、 *belowAvg.xsl*ファイルし、をクリックして**開く**です。

     XML エディターでスタイル シートが開きます。

3.  参照 ボタンをクリックして (**.**) で、**入力**ドキュメントのプロパティ ウィンドウのフィールドです。

4.  検索、 *books.xml*ファイルし、をクリックして**開く**です。

     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。

5.  右クリックし、`xsl:if`をポイントし、開始タグ**ブレークポイント**、 をクリック**ブレークポイントの挿入**です。

6.  クリックして、 **XSL のデバッグ**XML エディター ツールバーのボタンをクリックします。

これでデバッグ プロセスが開始され、デバッガーが使用する新しいウィンドウがいくつか開かれます。

入力ドキュメントとスタイル シートを表示するための 2 つのウィンドウがあります。 デバッガーはこれらのウィンドウを使って現在の実行状態を表示します。 デバッガーが配置されている、`xsl:if`要素内の最初の book ノードで、スタイル シートの*books.xml*ファイル。

**ローカル**ウィンドウは、すべてのローカル変数とその現在の値が表示されます。 ここには、スタイル シートで定義されている変数や、コンテキスト内に現在存在するノードを追跡するためにデバッガーが使用する変数なども表示されます。

**XSL Output**ウィンドウには、XSL 変換の出力が表示されます。 このウィンドウとは別の**Visual Studio の出力**ウィンドウです。

## <a name="watch-window"></a>[ウォッチ] ウィンドウ

### <a name="to-use-the-watch-window"></a>[ウォッチ] ウィンドウを使用するには

1.  **デバッグ** メニューのをポイント**Windows**、 をポイント**ウォッチ**、 をクリック**ウォッチ 1**です。

     これにより、**ウォッチ 1**  ウィンドウを表示します。

2.  型`$bookAverage`で、**名前**フィールドとキーを押して**Enter**です。

     ウィンドウに、`$bookAverage` 変数の値が表示されます。

3.  型`self::node()`で、**名前**フィールドとキーを押して**Enter**です。

     `self::node()` は、現在のコンテキスト ノードに評価される XPath 式です。 `self::node()` XPath 式の値は、最初の book ノードです。 この値は、変換処理の進行につれて変化します。

4.  `self::node()` ノードを展開して、`price` ノードを展開します。

     この操作によって書籍価格の値を確認できるので、その値を `$bookAverage` の値と容易に比較することができます。 この書籍価格は平均値より低いため、`xsl:if` 条件は成功するはずです。

## <a name="step-through-the-code"></a>コードをステップ実行
 デバッガーでは、コードを一度に 1 行ずつ実行することができます。

### <a name="to-step-through-the-code"></a>コードをステップ実行するには

1.  **F5** キーを押して続行します。

     最初の book ノードが満たされているため、`xsl:if`を book ノードに条件が追加、 **XSL Output**ウィンドウです。 デバッガーは、再度スタイル シートの `xsl:if` 要素に到達するまで、引き続き実行されます。 デバッガーは今すぐに 2 番目の book ノードに配置されている、 *books.xml*ファイル。

     **ウォッチ 1**ウィンドウ、`self::node()`値が 2 番目の book ノードに変更します。 price 要素の値を調べることで、価格が平均値より高いことを判断できるため、`xsl:if` 条件は失敗します。

2.  **F5** キーを押して続行します。

     2 番目の book ノードが満たしていないため、`xsl:if`条件には、book ノードは追加されません、 **XSL Output**ウィンドウです。 デバッガーは、再度スタイル シートの `xsl:if` 要素に到達するまで、引き続き実行されます。 デバッガーの 3 番目の位置は今すぐ`book`内のノード、 *books.xml*ファイル。

     **ウォッチ 1**ウィンドウ、`self::node()`値が 3 番目の book ノードに変更します。 `price` 要素の値を調べると、価格が平均値未満、つまり、`xsl:if` 条件が満たされていると判断できます。

3.  **F5** キーを押して続行します。

     `xsl:if`条件が満たされた、3 番目の book を追加する、 **XSL Output**ウィンドウです。 XML ドキュメント内の書籍がすべて処理され、デバッガーが停止します。

## <a name="sample-files"></a>サンプル ファイル

このチュートリアルでは、次の 2 つのファイルを使用します。

### <a name="belowavgxsl"></a>belowAvg.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>関連項目

- [XSLT のデバッグ](../xml-tools/debugging-xslt.md)