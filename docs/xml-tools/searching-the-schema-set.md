---
title: XML スキーマ エクスプ ローラーでスキーマ セットの検索
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1133d6a67442bde5a9f949553efcffd07e2d3ffe
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751742"
---
# <a name="search-the-schema-set"></a>スキーマ セットを検索します。

**XML スキーマ エクスプ ローラー**設定方法を次に、スキーマを検索することができます。

-   キーワード検索

-   スキーマ固有の検索

## <a name="keyword-search"></a>キーワード検索

 内の部分文字列を入力してキーワード検索を実行する、**検索 SchemaSet**のテキスト ボックス、 **XML スキーマ エクスプ ローラー**ツールバー。

 ![XML スキーマ エクスプローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif)

 **XML スキーマ エクスプ ローラー**スキーマ セットに、次の属性を検索します。

-   指定したキーワードに一致する `name` 属性または `ref` 属性。 名前では、要素、属性、型、およびを検索できます。

-   include ステートメントの `schemaLocation` 属性。

-   import ステートメントの `namespace` 属性。

## <a name="schema-specific-search"></a>スキーマ固有の検索

 **XML スキーマ エクスプ ローラー**のコンテキスト メニューを使用してアクセスできる組み込みの検索機能があります、 **XML スキーマ エクスプ ローラー**です。 使用できるコンテキスト メニューの詳細については、次を参照してください。[コンテキスト メニュー](../xml-tools/context-menus-xml-schema-explorer.md)です。 スタート ビューからスキーマに固有の検索を実行することもできます。詳細については、「スキーマ セットの詳細」セクションを参照してください、[スタート ビュー](../xml-tools/start-view.md)トピックです。

## <a name="display-and-navigate-search-results"></a>表示し、検索結果の移動

 検索が終了すると、ツール バーに概要結果ペインが追加され、検索結果が表示されます。 検索結果が強調表示も、 **XML スキーマ エクスプ ローラー**垂直スクロール バーのチックでマークされています。 使用して、検索結果を移動することができます、**次の検索結果に移動**と**前の検索結果に移動**、概要結果ペインの上のボタン、 **XML スキーマ エクスプ ローラー**ツールバーです。キーボードのキーを使用して、 **F3**と**shift キーを押し**+**F3**; か、スクロール バーの目盛りをクリックします。

 をクリックして、ワークスペースに検索結果を追加することができます、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。

 ![XML スキーマ エクスプローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>検索結果のクリア

 検索結果をクリアする をクリックして、 **x** 、概要結果ペインのボタン、 **XML スキーマ エクスプ ローラー**検索ツールバー。

## <a name="see-also"></a>関連項目

- [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)