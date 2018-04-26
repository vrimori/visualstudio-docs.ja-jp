---
title: XML エディターを使用して XML スキーマ デザイナーの統合
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2e2b7a9e6511faaa1941d65f6b328a07b10f79
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="integration-with-xml-editor"></a>XML エディターとの統合

XML スキーマ デザイナーは、XML エディターと統合されています。 変更が反映されますが、XML エディターの XSD ファイルを変更する場合、 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)です。 ある場合、[グラフ ビュー](../xml-tools/graph-view.md)または[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)開く、変更にも反映されますがあります。 次の方法を使用して XML スキーマ デザイナーと XML エディターの間を移動できます。

-   XML エディターで、ノードを右クリックし、選択**XML スキーマ エクスプ ローラーで表示**です。

-   グラフ ビューと XML スキーマ エクスプ ローラーで、ノードをダブルクリックまたはノードを右クリックし **コードの表示**です。 コンテンツ モデル ビューでノードを右クリックし、選択**コードの表示**です。

次のスクリーン ショットは、XML スキーマが表示されている XML スキーマ エクスプローラーを示しています。 XML スキーマ エクスプローラーでは、スキーマ セットがツリー ビューに表示されます。 XML エディターには、XML スキーマ エクスプローラーで現在アクティブになっているノードのテキスト ビューが表示されます。

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

場合によっては、XML エディターとグラフィカルなデザイナーのコードを並べて表示すると便利です。 を同時に両方のファイルを表示する XML エディターで任意の場所を右クリックし、選択**ビュー デザイナー**です。 Visual Studio Windows メニューで、次のように選択します。**新しい水平 (または垂直) タブ グループ**です。

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>関連項目

- [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)