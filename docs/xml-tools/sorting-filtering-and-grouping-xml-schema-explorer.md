---
title: 並べ替え、フィルター、およびグループ化 (XML スキーマ エクスプ ローラー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad8225ae325c453836f5c7bcf7fb6ac0c5fb04a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>並べ替え、フィルター処理、およびグループ化 (XML スキーマ エクスプローラー)
このトピックで使用できるオプションについて説明、**並べ替え、フィルター処理、およびグループ化のオプション**XML スキーマ エクスプ ローラー ツールバーのメニュー。  
  
## <a name="filter-options"></a>フィルター オプション  
 次のフィルター オプションがあります。 既定では、**名前空間の表示**と**スキーマ ファイルを表示**オプションを選択します。  
  
-   **名前空間を表示する**です。  
  
-   **スキーマ ファイルを表示する**です。  
  
-   **(シーケンスまたは選択肢/すべて) コンポジターの表示**です。  
  
## <a name="sorting-options"></a>並べ替えオプション  
 次の並べ替えオプションがあります。 既定値は**種類で並べ替え**です。 ファイルと名前空間には、[種類で並べ替え] オプションと [名前で並べ替え] オプションは適用されません。  
  
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
  
## <a name="persisting-sortfilter-options"></a>並べ替え/フィルター オプションの保存  
 設定の変更時に開かれていたソリューションやファイルにかかわらず、並べ替え、フィルター処理、およびグループ化のオプションは各ユーザーのレジストリに保存されます。