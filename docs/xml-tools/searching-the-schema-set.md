---
title: XML スキーマ エクスプ ローラーでスキーマ セットの検索
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99e8c8301f057990471ff9b20f782a4c3ee13fb1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992179"
---
# <a name="search-the-schema-set"></a>スキーマ セットを検索します。

**XML スキーマ エクスプ ローラー**次の方法でスキーマ セットを検索することができます。

-   キーワード検索

-   スキーマ固有の検索

## <a name="keyword-search"></a>キーワード検索

 内の部分文字列を入力してキーワード検索を実行する、**検索 SchemaSet**のテキスト ボックス、 **XML スキーマ エクスプ ローラー**ツールバー。

 ![XML スキーマ エクスプローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif)

 **XML スキーマ エクスプ ローラー**スキーマは次の属性のセットを検索します。

-   指定したキーワードに一致する `name` 属性または `ref` 属性。 名前では、要素、属性、型、およびを見つけることができます。

-   include ステートメントの `schemaLocation` 属性。

-   import ステートメントの `namespace` 属性。

## <a name="schema-specific-search"></a>スキーマ固有の検索

 **XML スキーマ エクスプ ローラー**のコンテキスト (右クリック) メニューを使用してアクセスできる組み込みの検索機能もあります、 **XML スキーマ エクスプ ローラー**します。 使用できるコンテキスト メニューの詳細については、次を参照してください。[コンテキスト メニュー](../xml-tools/context-menus-xml-schema-explorer.md)します。 スタート ビューからスキーマ固有の検索を実行することもできます。詳細については、「スキーマ セットの詳細」セクションを参照してください、[スタート ビュー](../xml-tools/start-view.md)トピック。

## <a name="display-and-navigate-search-results"></a>表示し、検索結果を移動します。

 検索が終了すると、ツール バーに概要結果ペインが追加され、検索結果が表示されます。 検索結果はでも強調表示、 **XML スキーマ エクスプ ローラー**垂直スクロール バーのチックでマークされているとします。 使用して、検索結果を移動することができます、**次の検索結果に移動して**と**前の検索結果に移動して**ボタンの概要結果ペインで、 **XML スキーマ エクスプ ローラー**ツールバーです。キーボードのキーを使用して**F3**と**Shift**+**F3**; またはスクロール バーの目盛りをクリックしています。

 クリックして、ワークスペースに検索結果を追加することができます、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。

 ![XML スキーマ エクスプローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>検索結果のクリア

 検索結果をクリアするには、クリックして、 **x**の概要結果ペインのボタン、 **XML スキーマ エクスプ ローラー**サーチ ツールバー。

## <a name="see-also"></a>関連項目

- [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)