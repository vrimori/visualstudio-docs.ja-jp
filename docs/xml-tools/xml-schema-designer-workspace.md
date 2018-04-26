---
title: XML スキーマ デザイナーのワークスペース
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 588fa495-fe7f-4b16-8a9f-6b6b8d2d502a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c787431cbdf9f6a9bcb70a87b99b0a566fd0e5ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="xml-schema-designer-workspace"></a>XML スキーマ デザイナーのワークスペース

XML スキーマ デザイナー (XSD デザイナー) は、XML スキーマを調べるために使用できるグラフィカル ツールです。 加え、 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)を参照し、XML スキーマのツリーを移動し、検索を実行することができます、XSD デザイナーには、使用すると、XSD スキーマをさらに詳しく調べる 3 つのビューが用意されています。 スタート ビューは XSD デザイナーの起点で、スタート ビューからは、XSD デザイナーの他のビューに移動したり、スキーマ セットの詳細を表示したりすることができます。 グラフ ビューでは、スキーマ セットの概要とスキーマ ノード間のリレーションシップを表示できます。 コンテンツ モデル ビューには、単純型、複合型、要素、グループ、属性、属性グループなど、ローカル スキーマ ノードとグローバル スキーマ ノードの詳細がグラフィック表示されます。

目的のノードを調べるには、ワークスペースにノードを追加する必要があります。 ワークスペースは、すべてのビューで共有されます。

## <a name="adding-nodes-to-the-workspace"></a>ワークスペースへのノードの追加

次の方法でワークスペースにノードを追加できます。

-   「スキーマ セットの詳細」セクションで、[スタート ビュー](../xml-tools/start-view.md)、をクリックして、**追加**グローバル ノードの種類の横にあるリンクします。

-   XML スキーマ エクスプローラーからは、3 つのどのビューにでもグローバル ノード、ファイル ノード、および名前空間ノードをドラッグ アンド ドロップすることができます。 詳細についてを参照してください「ノードをドラッグすること、および削除する」 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)です。

-   XML スキーマ エクスプローラーのコンテキスト メニューを使用します。 詳細については、次を参照してください。[コンテキスト メニュー](../xml-tools/context-menus-xml-schema-explorer.md)です。

-   XSD エクスプ ローラーで検索を実行し、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。 詳細については、次を参照してください。[スキーマ セットの検索](../xml-tools/searching-the-schema-set.md)です。

## <a name="view-switching"></a>ビューの切り替え

ビューを切り替えるには、次のいずれかを使用します。

-   XSD デザイナーのツール バー。

-   コンテンツ モデル ビューおよびグラフ ビューのコンテキスト メニュー

-   スタート ビューのウォーターマークか、空白のコンテンツ モデル ビューまたはグラフ ビューのウォーターマーク。

-   ホット キー: スタート ビューに切り替えるには Ctrl + 1、グラフ ビューに切り替えるには Ctrl + 2、およびコンテンツ モデル ビューに切り替えるには Ctrl + 3。