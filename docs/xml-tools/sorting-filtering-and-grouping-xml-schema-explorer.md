---
title: 並べ替え、フィルター処理、および XML スキーマ エクスプ ローラーでグループ化
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a3e281f8e3995cf22100d328089f1993110f756
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693670"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>並べ替え、フィルター、およびグループ化 (XML スキーマ エクスプ ローラー)

このトピックで使用できるオプションについて説明、**並べ替え、フィルター処理、およびグループ化のオプション**メニューで、 **XML スキーマ エクスプ ローラー**ツールバー。

## <a name="filter-options"></a>フィルター オプション

 次のフィルター オプションがあります。 既定では、**名前空間の表示**と**スキーマ ファイルを表示**オプションを選択します。

-   **名前空間を表示する**です。

-   **スキーマ ファイルを表示する**です。

-   **(シーケンスまたは選択肢/すべて) コンポジターの表示**です。

## <a name="sorting-options"></a>並べ替えオプション

 次の並べ替えオプションがあります。 既定値は**種類で並べ替え**です。 **並べ替えによって**オプションは、ファイルと名前空間には適用されません。

-   **型で並べ替え**です。

-   **名前順で並べ替え**です。

-   **ドキュメントの順序**です。

### <a name="sort-by-type"></a>[種類で並べ替え]

 ときに、**種類で並べ替え**オプションが選択されている場合、グローバル ノードが次の順序で並べ替えられます。 さらに、各グループ内でアルファベット順に並べ替えられます。

1.  `import` ノード

2.  `include` ノード

3.  `redefine` ノード

4.  `attribute` ノード

5.  `attributeGroup` ノード

6.  `complexType` ノード

7.  `simpleType` ノード

8.  `element` ノード

9. `group` ノード

### <a name="sort-by-name"></a>[名前で並べ替え]

 ときに、**名前順で並べ替え**オプションが選択されている場合、グローバル ノードが次の順序で並べ替えられます。

1.  `import` ノード (名前空間のアルファベット順)

2.  `include` ノード (`schemaLocation` 属性のアルファベット順)

3.  `redefine` ノード (`schemaLocation` 属性のアルファベット順)

4.  その他のグローバル ノード (アルファベット順)

### <a name="document-order"></a>[ドキュメントの順序]

 **ドキュメント順**オプションは使用可能な場合に、**スキーマ ファイルを表示**オプションを選択します。 ときに**ドキュメント順**が選択されているグローバル ノードが、スキーマ ファイルで表示される順に表示されます。

## <a name="persisting-sortfilter-options"></a>永続化の並べ替え/フィルター オプション

 設定の変更時に開かれていたソリューションやファイルにかかわらず、並べ替え、フィルター処理、およびグループ化のオプションは各ユーザーのレジストリに保存されます。