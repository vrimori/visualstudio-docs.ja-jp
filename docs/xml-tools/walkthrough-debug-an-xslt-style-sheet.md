---
title: "チュートリアル : XSLT スタイル シートのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# チュートリアル : XSLT スタイル シートのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルの手順では、XSLT デバッガーを使用する方法を示します。変数の表示、ブレークポイントの設定、コードのステップ実行などの手順が含まれます。このスタイル シートでは、平均書籍価格を下回るすべての書籍が検索されます。  
  
### このチュートリアルの準備をするには  
  
1.  開かれているソリューションをすべて閉じます。  
  
2.  2 つのサンプル ファイルをローカル コンピューターにコピーします。  
  
## デバッグの開始  
  
#### デバッグを開始するには  
  
1.  \[ファイル\] メニューの \[開く\] をポイントし、\[ファイル\] をクリックします。  
  
2.  belowAvg.xsl ファイルを見つけ、\[開く\] をクリックします。  
  
     XML エディターでスタイル シートが開きます。  
  
3.  ドキュメントのプロパティ ウィンドウの \[入力\] フィールドで、参照ボタン \(\[...\]\) をクリックします。  
  
4.  books.xml ファイルを見つけ、\[開く\] をクリックします。  
  
     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。  
  
5.  \[`xsl:if`\] 開始タグを右クリックし、\[ブレークポイント\] をポイントします。次に、\[ブレークポイントの挿入\] をクリックします。  
  
6.  XML エディター ツール バーの \[Debug XSL \(XSL のデバッグ\)\] ボタンをクリックします。  
  
 これでデバッグ プロセスが開始され、デバッガーが使用する新しいウィンドウがいくつか開かれます。  
  
 入力ドキュメントとスタイル シートを表示するための 2 つのウィンドウがあります。デバッガーはこれらのウィンドウを使って現在の実行状態を表示します。デバッガーの位置は、スタイル シートの `xsl:if` 要素および books.xml ファイルの最初の book ノードです。  
  
 \[ローカル\] ウィンドウには、すべてのローカル変数と、それらの現在の値が表示されます。ここには、スタイル シートで定義されている変数や、コンテキスト内に現在存在するノードを追跡するためにデバッガーが使用する変数なども表示されます。  
  
 \[XSL Output\] ウィンドウに、XSL 変換の出力が表示されます。これは、\[Visual Studio Output \(Visual Studio 出力\)\] ウィンドウとは別のウィンドウです。  
  
## \[ウォッチ\] ウィンドウ  
  
#### \[ウォッチ\] ウィンドウを使用するには  
  
1.  \[デバッグ\] メニューの \[ウィンドウ\] をポイントし、\[ウォッチ\] をクリックします。次に、\[ウォッチ 1\] をクリックします。  
  
     これで \[ウォッチ 1\] ウィンドウが表示されます。  
  
2.  \[名前\] フィールドに「`$bookAverage`」と入力し、**Enter** キーを押します。  
  
     ウィンドウに、`$bookAverage` 変数の値が表示されます。  
  
3.  \[名前\] フィールドに「`self::node()`」と入力し、**Enter** キーを押します。  
  
     `self::node()` は、現在のコンテキスト ノードに評価される XPath 式です。`self::node()` XPath 式の値は、最初の book ノードです。この値は、変換処理の進行につれて変化します。  
  
4.  `self::node()` ノードを展開して、`price` ノードを展開します。  
  
     この操作によって書籍価格の値を確認できるので、その値を `$bookAverage` の値と容易に比較することができます。この書籍価格は平均値より低いため、`xsl:if` 条件は成功するはずです。  
  
## コードのステップ実行  
 デバッガーでは、コードを一度に 1 行ずつ実行することができます。  
  
#### コードをステップ実行するには  
  
1.  **F5** キーを押して続行します。  
  
     最初の book ノードは `xsl:if` 条件を満たしたため、この book ノードは \[XSL Output\] ウィンドウに追加されます。デバッガーは、再度スタイル シートの `xsl:if` 要素に到達するまで、引き続き実行されます。今度は、デバッガーが、books.xml ファイルの 2 番目の book ノードに到達して中断します。  
  
     \[ウォッチ 1\] ウィンドウでは、`self::node()` の値が 2 番目の book ノードに変化します。price 要素の値を調べることで、価格が平均値より高いことを判断できるため、`xsl:if` 条件は失敗します。  
  
2.  **F5** キーを押して続行します。  
  
     2 番目の book ノードは `xsl:if` 条件を満たしていないため、この book ノードは \[XSL Output\] ウィンドウに追加されません。デバッガーは、再度スタイル シートの `xsl:if` 要素に到達するまで、引き続き実行されます。今度は、デバッガーが、books.xml ファイルの 3 番目の `book` ノードに到達して中断します。  
  
     \[ウォッチ 1\] ウィンドウでは、`self::node()` の値が 3 番目の book ノードに変化します。`price` 要素の値を調べると、価格が平均値未満、つまり、`xsl:if` 条件が満たされていると判断できます。  
  
3.  **F5** キーを押して続行します。  
  
     `xsl:if` 条件が満たされたため、3 番目の book ノードは \[XSL Output \(XSL 出力\)\] ウィンドウに追加されます。XML ドキュメント内の書籍がすべて処理され、デバッガーが停止します。  
  
## サンプル ファイル  
 このチュートリアルでは、次の 2 つのファイルを使用します。  
  
### belowAvg.xsl  
  
```  
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
  
### books.xml  
  
```  
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
  
## 参照  
 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)