---
title: 'チュートリアル: XSLT 階層の使用'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 20223a18fa422facc7d7a0a74336402d6d391b0a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693446"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>チュートリアル: を使用して XSLT 階層

XSLT 階層ツールは、多くの XML 開発タスクを簡素化します。 XSLT スタイル シートには、多くの場合 `includes` 命令および `imports` 命令が使用されています。 コンパイルはプリンシパル スタイル シートから開始されますが、XSLT スタイル シートのコンパイル結果としてエラーが表示された場合、プリンシパル スタイル シート以外のものがエラーの原因である可能性があります。 エラーを修正するか、スタイル シートを編集するには、インクルードまたはインポートされたスタイル シートへのアクセスが必要になる場合があります。 デバッガーでスタイル シートをステップ実行すると、インクルードまたはインポートされたスタイル シートが開かれる場合があり、1 つまたは複数のインクルードされたスタイル シートにブレークポイントを追加することができます。

XSLT 階層ツールが役立つ別のシナリオとして、ビルトイン テンプレート規則にブレークポイントを挿入することがあります。 テンプレート規則は、スタイル シートの各モードに対して生成される特別なテンプレートであり、ノードに該当するテンプレートが他にない場合に、`xsl:apply-templates` により呼び出されます。 ビルトイン テンプレート規則でデバッグを実行するには、XSLT デバッガーで一時フォルダーに規則のファイルを作成し、プリンシパル スタイル シートと共にコンパイルします。 何らかの `xsl:apply-template` からコードへのステップ インを実行しないと、プリンシパル スタイル シートにインクルードされたスタイル シートを探したり、ビルトイン テンプレート規則を持つスタイル シートを探して開くことが困難になる場合があります。

このトピックの例には、参照されるスタイル シート内のデバッグが示されています。

## <a name="to-debug-in-a-referenced-style-sheet"></a>参照されるスタイル シートをデバッグするには

1. Visual Studio で XML ドキュメントを開きます。 この例では、次のドキュメントを使用します。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. 次の追加*xslincludefile.xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3.  次の追加*xslinclude.xsl*ファイル。

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4.  命令にブレークポイントを追加`<xsl:include href="xslincludefile.xsl" />`です。

5.  デバッグを開始します。

6.  命令でデバッガーを停止するときに`<xsl:include href="xslincludefile.xsl" />`、キーを押して、**ステップ イン**ボタンをクリックします。 参照されるスタイル シートのデバッグを続行できます。 階層が表示され、デザイナーに正しいパスが示されます。

## <a name="see-also"></a>関連項目

- [チュートリアル: XSLT プロファイラー](../xml-tools/walkthrough-xslt-profiler.md)