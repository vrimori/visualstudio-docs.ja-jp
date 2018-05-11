---
title: Visual Studio の XML ツール
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 279a0a73f24b2916e21293c854692ab40f444b4c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio の XML ツール

*拡張マークアップ言語 (XML)* データを記述するため、形式を提供するマークアップ言語です。 これにより、コンテンツの宣言がより正確になり、複数のプラットフォームをまたいだ検索結果がよりわかりやすくなります。 さらに、XML では、データと表示形式とを切り離すことができます。 たとえば、HTML では、ブラウザーでの太字や斜体によるデータの表示をタグで指定します。XML では、市の名前、気温、気圧などのデータを記述する目的でのみタグを使用します。 XML では、拡張スタイルシート言語 (XSL) やカスケード スタイル シート (CSS) などのスタイル シートを使用して、ブラウザーにデータを表示します。 XML では、データが表示形式と処理から切り離されます。 このため、適用するスタイル シートやアプリケーションを変えることによって、データの表示や処理を思いどおりに行うことができます。

XML は SGML のサブセットで、Web を通じて送信するために最適化されています。 これは W3C (World Wide Web Consortium) が定義したものです。 この標準化によって、アプリケーションや販売元から独立している統一形式の構造化データを作成できます。

XML では、Visual Studio と .NET Framework のさまざまな機能の中核になります。 次のトピック一覧のツールと Visual Studio と .NET Framework で提供されている XML に関連する機能を名前します。

詳細については、次を参照してください。、<xref:System.Xml?displayProperty=fullName>ドキュメント。

## <a name="reference"></a>参照

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)公開、 [XML エディター](http://go.microsoft.com/fwlink/?LinkId=228249)パース ツリーを[System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) XML ドキュメントです。

[XML 標準のリファレンス](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)XML、ドキュメント型定義 (DTD)、XML スキーマ定義言語 (XSD) および XSLT などの XML テクノロジに関する情報を提供します。

<xref:System.Xml?displayProperty=fullName> クラスとその他の要素を構成するについて説明します、<xref:System.Xml>名前空間の各項目に詳細情報へのリンクを示します。

<xref:System.Xml.Serialization?displayProperty=fullName> クラスとその他の要素を構成するについて説明します、<xref:System.Xml.Serialization>名前空間の各項目に関する詳細情報へのリンクを示します。

## <a name="related-sections"></a>関連項目

[XML ドキュメント オブジェクト モデル (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)について説明する方法、<xref:System.Xml.XmlDocument>とその関連クラスは、W3C ドキュメント オブジェクト モデル (Core) Level 1 および第 2 レベルの名前空間サポート仕様に準拠します。

[XmlReader および XmlWriter による XML データの処理](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[XSLT 変換](/dotnet/standard/data/xml/xslt-transformations)について説明する方法、<xref:System.Xml.Xsl.XslCompiledTransform>クラスは、XSLT 1.0 勧告を実装します。

[XPath データ モデルを使用して XML データを処理](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)説明方法、<xref:System.Xml.XPath.XPathNavigator>クラスに格納された XML データを処理できる、<xref:System.Xml.XPath.XPathDocument>または<xref:System.Xml.XmlDocument>オブジェクト。 <xref:System.Xml.XPath.XPathNavigator> クラスは XQuery 1.0 および XPath 2.0 のデータ モデルに基づいており、XML データの操作と編集に使用できます。

[XML スキーマ オブジェクト モデル (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)の作成と提供することにより、XML スキーマを操作に使用されるクラスについて説明します、<xref:System.Xml.Schema.XmlSchema>の読み込みし、スキーマを編集するクラス。