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
ms.openlocfilehash: 317588e4d6c81a13a18c036a040508a1adebafcb
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
---
# <a name="xml-schema-designer-workspace"></a>XML スキーマ デザイナーのワークスペース

XML スキーマ デザイナー (XSD デザイナー) は、XML スキーマを調べるために使用できるグラフィカル ツールです。 加え、 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)を参照し、XML スキーマのツリーを移動し、検索を実行することができます、XSD デザイナーには、使用すると、XSD スキーマをさらに詳しく調べる 3 つのビューが用意されています。 スタート ビューは XSD デザイナーの起点で、スタート ビューからは、XSD デザイナーの他のビューに移動したり、スキーマ セットの詳細を表示したりすることができます。 グラフ ビューでは、スキーマ セットの概要とスキーマ ノード間のリレーションシップを表示できます。 コンテンツ モデル ビューには、単純型、複合型、要素、グループ、属性、属性グループなど、ローカル スキーマ ノードとグローバル スキーマ ノードの詳細がグラフィック表示されます。

目的のノードを調べるには、ワークスペースにノードを追加する必要があります。 ワークスペースは、すべてのビューで共有されます。

## <a name="add-nodes-to-the-workspace"></a>ワークスペースにノードを追加します。

次の方法でワークスペースにノードを追加できます。

-   「スキーマ セットの詳細」セクションで、[スタート ビュー](../xml-tools/start-view.md)、をクリックして、**追加**グローバル ノードの種類の横にあるリンクします。

-   ドラッグ アンド ドロップのグローバル ノード、ファイル ノード、および名前空間ノードから、 **XML スキーマ エクスプ ローラー**に 3 つのビューのいずれか。 詳細についてを参照してください「ノードをドラッグすること、および削除する」 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)です。

-   コンテキスト メニューを使用して、 **XML スキーマ エクスプ ローラー**です。 詳細については、次を参照してください。[コンテキスト メニュー](../xml-tools/context-menus-xml-schema-explorer.md)です。

-   XSD エクスプ ローラーで検索を実行し、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。 詳細については、次を参照してください。[スキーマ セットの検索](../xml-tools/searching-the-schema-set.md)です。

## <a name="switch-views"></a>ビューを切り替える

ビューを切り替えるには、次のいずれかを使用します。

-   XSD デザイナーのツール バー。

-   コンテンツ モデル ビューおよびグラフ ビューのコンテキスト メニュー

-   スタート ビューのウォーターマークか、空白のコンテンツ モデル ビューまたはグラフ ビューのウォーターマーク。

-   ホット キー: **Ctrl**+**1**スタート ビューの**Ctrl**+**2**グラフ ビューのおよび**Ctrl キーを押し**+**3**コンテンツ モデル ビューにします。