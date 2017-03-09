---
title: "Visual Studio の XML ツール | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "クラス [Visual Studio], XML"
  - "CSS, スタイル シート (XML の)"
  - "データ [Visual Studio], XML"
  - "データセット [Visual Basic], XML スキーマ"
  - "探索ファイル, XML"
  - "エンタープライズ テンプレート, XML および"
  - "サーバー コントロール, XML および"
  - "SGML, XML"
  - "スタイル シート, XML 用"
  - "Web サーバー コントロール, XML"
  - "Web サービス"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], .NET Framework クラス"
  - "XML [Visual Studio], データ ソース"
  - "XML [Visual Studio], リソース"
  - "XML [Visual Studio], SGML の関係"
  - "XML スキーマ"
  - "XMLDataDocument クラス"
  - "XSD スキーマ"
  - "XSL"
  - "XSL, スタイル シート"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual Studio の XML ツール
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*XML \(Extensible Markup Language\)* は、データの記述形式を定めたマークアップ言語です。  これにより、コンテンツの宣言がより正確になり、複数のプラットフォームをまたいだ検索結果がよりわかりやすくなります。  さらに、XML では、データと表示形式とを切り離すことができます。  たとえば、HTML では、ブラウザーでの太字や斜体によるデータの表示をタグで指定します。XML では、市の名前、気温、気圧などのデータを記述する目的でのみタグを使用します。  XML では、拡張スタイルシート言語 \(XSL\) やカスケード スタイル シート \(CSS\) などのスタイル シートを使用して、ブラウザーにデータを表示します。  XML では、データが表示形式と処理から切り離されます。  このため、適用するスタイル シートやアプリケーションを変えることによって、データの表示や処理を思いどおりに行うことができます。  
  
 XML は SGML のサブセットで、Web を通じて送信するために最適化されています。  これは W3C \(World Wide Web Consortium\) が定義したものです。  この標準化によって、アプリケーションや販売元から独立している統一形式の構造化データを作成できます。  
  
 XML は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] および [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の多くの機能の中核となっています。  次のトピック一覧に、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] および [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] で提供される XML 関連のツールと機能を示します。  
  
 詳細については、XML 開発者向けの最新ドキュメント、技術情報、ダウンロード、ニュースグループ、およびその他のリソースが提供されている[XML のデベロッパー センター](http://go.microsoft.com/fwlink/?LinkID=100176)を参照してください。  
  
## このセクションの内容  
 [XML データの使用](../xml-tools/working-with-xml-data.md)  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でデータを処理する際の XML の役割について説明します。  
  
 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)  
 Visual Studio デバッガーを使用した XSLT のデバッグに関するトピックへのリンクを示します。  
  
## 関連項目  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 [XML エディター](http://go.microsoft.com/fwlink/?LinkId=228249)のパース ツリーを XML ドキュメントの [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) を介して公開します。  
  
 [XML 標準のリファレンス](http://msdn.microsoft.com/ja-jp/79c78508-c9d0-423a-a00f-672e855de401)  
 XML、DTD \(Document Type Definition\)、XSD \(XML Schema Definition\) 言語、XSLT などの XML テクノロジについて説明します。  
  
 <xref:System.Xml?displayProperty=fullName>  
 <xref:System.Xml> 名前空間を構成するクラスと他の要素について説明し、項目ごとに詳細説明へのリンクを示します。  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 <xref:System.Xml.Serialization> 名前空間を構成するクラスと他の要素について説明し、項目ごとに詳細説明へのリンクを示します。  
  
## 関連項目  
 [XML ドキュメント オブジェクト モデル \(DOM\)](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 <xref:System.Xml.XmlDocument> とその関連クラスが W3C の Document Object Model \(Core\) Level 1 および Level 2 の名前空間サポート仕様にどのように準拠しているかを説明します。  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/ja-jp/3029834c-a27e-4331-b7aa-711924062182)  
 XML ストリームの XML データに対して、<xref:System.Xml.XmlReader> でキャッシュを利用せずに順方向限定の読み取り専用アクセスを行う方法について説明します。  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/ja-jp/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 <xref:System.Xml.XmlWriter> を使用して、キャッシュを利用せずに順方向限定で XML ストリームを生成する方法について説明し、W3C 標準準拠の XML ドキュメントの作成に役立つ情報を示します。  
  
 [XSLT 変換](../Topic/XSLT%20Transformations.md)  
 <xref:System.Xml.Xsl.XslCompiledTransform> クラスが XSLT 1.0 勧告を実装する方法について説明します。  
  
 [XPath データ モデルを使用した XML データの処理](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 <xref:System.Xml.XPath.XPathNavigator> クラスが <xref:System.Xml.XPath.XPathDocument> オブジェクトや <xref:System.Xml.XmlDocument> オブジェクトに格納された XML データを処理する方法について説明します。  <xref:System.Xml.XPath.XPathNavigator> クラスは XQuery 1.0 および XPath 2.0 のデータ モデルに基づいており、XML データの操作と編集に使用できます。  
  
 [XML スキーマ オブジェクト モデル \(SOM\)](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 スキーマの読み込みと編集を行う <xref:System.Xml.Schema.XmlSchema> クラスを例に取り上げ、XML スキーマの作成と操作に使用するクラスについて説明します。