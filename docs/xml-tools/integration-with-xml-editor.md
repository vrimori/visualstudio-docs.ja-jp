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
ms.openlocfilehash: 3ae7595121fcefa36998a88b53aae466d3a726cb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573324"
---
# <a name="integration-with-xml-editor"></a>XML エディターとの統合

XML スキーマ デザイナーは、XML エディターと統合されています。 変更が反映されますが、XML エディターの XSD ファイルを変更する場合、 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)です。 ある場合、[グラフ ビュー](../xml-tools/graph-view.md)または[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)開く、変更にも反映されますがあります。 次の方法を使用して XML スキーマ デザイナーと XML エディターの間を移動できます。

-   XML エディターで、ノードを右クリックし、選択**XML スキーマ エクスプ ローラーで表示**です。

-   グラフ ビューで、 **XML スキーマ エクスプ ローラー**、ノードをダブルクリックして、またはノードを右クリックし、選択**コードの表示**です。 コンテンツ モデル ビューでノードを右クリックし、選択**コードの表示**です。

次のスクリーン ショットで開かれている XML スキーマを示しています、 **XML スキーマ エクスプ ローラー**です。 **XML スキーマ エクスプ ローラー**スキーマ ツリー ビューのセットが表示されます。 XML エディターで現在アクティブなノードのテキスト ビューを表示する、 **XML スキーマ エクスプ ローラー**です。

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

場合によっては、XML エディターとグラフィカルなデザイナーのコードを並べて表示すると便利です。 を同時に両方のファイルを表示する XML エディターで任意の場所を右クリックし、選択**ビュー デザイナー**です。 Visual Studio Windows メニューで、次のように選択します。**新しい水平 (または垂直) タブ グループ**です。

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>関連項目

- [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)