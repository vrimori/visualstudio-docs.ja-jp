---
title: 並べ替え、フィルター処理、およびグループ化 (XML スキーマ エクスプ ローラー) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9cb8086e894130fa20f8c270c9dafe6b302c989c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545483"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>並べ替え、フィルター処理、およびグループ化 (XML スキーマ エクスプローラー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[並べ替え、フィルター処理、およびグループ化 (XML スキーマ エクスプ ローラー)](https://docs.microsoft.com/visualstudio/xml-tools/sorting-filtering-and-grouping-xml-schema-explorer)します。  
  
  
ここで使用できるオプションについて説明、**並べ替え、フィルター処理、およびグループ化のオプション**XML スキーマ エクスプ ローラー ツールバーのメニュー。  
  
## <a name="filter-options"></a>フィルター オプション  
 次のフィルター オプションがあります。 既定では、**名前空間の表示**と**スキーマ ファイルの**のオプションを選択します。  
  
-   **名前空間の表示**します。  
  
-   **スキーマ ファイルを表示する**します。  
  
-   **(シーケンス/選択/すべて) の表示 (sequence/choice/all)** します。  
  
## <a name="sorting-options"></a>並べ替えオプション  
 次の並べ替えオプションがあります。 既定値は**種類で並べ替え**します。 ファイルと名前空間には、[種類で並べ替え] オプションと [名前で並べ替え] オプションは適用されません。  
  
-   **種類で並べ替え**します。  
  
-   **名前順で並べ替え**します。  
  
-   **ドキュメント順**します。  
  
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
 ときに、**名前で並べ替え**オプションが選択されている場合、グローバル ノードが次の順序で並べ替えられます。  
  
1.  `import` ノード (名前空間のアルファベット順)  
  
2.  `include` ノード (`schemaLocation` 属性のアルファベット順)  
  
3.  `redefine` ノード (`schemaLocation` 属性のアルファベット順)  
  
4.  その他のグローバル ノード (アルファベット順)  
  
### <a name="document-order"></a>[ドキュメントの順序]  
 **ドキュメント順**場合オプションは使用、 **スキーマ ファイルの**オプションを選択します。 ときに**ドキュメント順**が選択されているスキーマ ファイルに出現する順序でのグローバル ノードが表示されます。  
  
## <a name="persisting-sortfilter-options"></a>並べ替え/フィルター オプションの保存  
 設定の変更時に開かれていたソリューションやファイルにかかわらず、並べ替え、フィルター処理、およびグループ化のオプションは各ユーザーのレジストリに保存されます。





