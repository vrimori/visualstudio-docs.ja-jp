---
title: "Visual Studio での XML ツール |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38d933199c85bee3fa85a533f9c61c08bee898ea
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio の XML ツール

*拡張マークアップ言語 (XML)*データを記述するため、形式を提供するマークアップ言語です。 これにより、コンテンツの宣言がより正確になり、複数のプラットフォームをまたいだ検索結果がよりわかりやすくなります。 さらに、XML では、データと表示形式とを切り離すことができます。 たとえば、HTML では、ブラウザーでの太字や斜体によるデータの表示をタグで指定します。XML では、市の名前、気温、気圧などのデータを記述する目的でのみタグを使用します。 XML では、拡張スタイルシート言語 (XSL) やカスケード スタイル シート (CSS) などのスタイル シートを使用して、ブラウザーにデータを表示します。 XML では、データが表示形式と処理から切り離されます。 このため、適用するスタイル シートやアプリケーションを変えることによって、データの表示や処理を思いどおりに行うことができます。

XML は SGML のサブセットで、Web を通じて送信するために最適化されています。 これは W3C (World Wide Web Consortium) が定義したものです。 この標準化によって、アプリケーションや販売元から独立している統一形式の構造化データを作成できます。

XML では、Visual Studio と .NET Framework のさまざまな機能の中核になります。 次のトピック一覧のツールと Visual Studio と .NET Framework で提供されている XML に関連する機能を名前します。

詳細については、次を参照してください。、<xref:System.Xml?displayProperty=fullName>ドキュメント。

## <a name="in-this-section"></a>このセクションの内容

[XML データの使用](../xml-tools/working-with-xml-data.md)  
Visual Studio でのデータ処理の方法で XML の役割について説明します。

[XSLT のデバッグ](../xml-tools/debugging-xslt.md)  
Visual Studio デバッガーを使用した XSLT のデバッグに関するトピックへのリンクを示します。

## <a name="reference"></a>参照

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
公開、 [XML エディター](http://go.microsoft.com/fwlink/?LinkId=228249)パース ツリーを[System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) XML ドキュメントです。

[XML 標準のリファレンス](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)  
XML、DTD (Document Type Definition)、XSD (XML Schema Definition) 言語、XSLT などの XML テクノロジについて説明します。

<xref:System.Xml?displayProperty=fullName>  
<xref:System.Xml> 名前空間を構成するクラスと他の要素について説明し、項目ごとに詳細説明へのリンクを示します。

<xref:System.Xml.Serialization?displayProperty=fullName>  
<xref:System.Xml.Serialization> 名前空間を構成するクラスと他の要素について説明し、項目ごとに詳細説明へのリンクを示します。

## <a name="related-sections"></a>関連項目

[XML ドキュメント オブジェクト モデル (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)  
<xref:System.Xml.XmlDocument> とその関連クラスが W3C の Document Object Model (Core) Level 1 および Level 2 の名前空間サポート仕様にどのように準拠しているかを説明します。

[XmlReader および XmlWriter による XML データの処理](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[XSLT 変換](/dotnet/standard/data/xml/xslt-transformations)  
<xref:System.Xml.Xsl.XslCompiledTransform> クラスが XSLT 1.0 勧告を実装する方法について説明します。

[XPath データ モデルを使用した XML データの処理](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
<xref:System.Xml.XPath.XPathNavigator> クラスが <xref:System.Xml.XPath.XPathDocument> オブジェクトや <xref:System.Xml.XmlDocument> オブジェクトに格納された XML データを処理する方法について説明します。 <xref:System.Xml.XPath.XPathNavigator> クラスは XQuery 1.0 および XPath 2.0 のデータ モデルに基づいており、XML データの操作と編集に使用できます。

[XML スキーマ オブジェクト モデル (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)  
スキーマの読み込みと編集を行う <xref:System.Xml.Schema.XmlSchema> クラスを例に取り上げ、XML スキーマの作成と操作に使用するクラスについて説明します。