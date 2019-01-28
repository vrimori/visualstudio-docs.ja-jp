---
title: XML エディターと XML スキーマ デザイナーの統合
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e2cb44f3416aabfa859d4a8ef2126003b3ce59e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992127"
---
# <a name="integration-with-xml-editor"></a>XML エディターとの統合

XML スキーマ デザイナーは、XML エディターと統合されています。 変更を反映する、XML エディターで XSD ファイルを変更する場合、 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)します。 ある場合、[グラフ ビュー](../xml-tools/graph-view.md)または[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)開く、変更も反映されますがあります。 次の方法を使用して XML スキーマ デザイナーと XML エディターの間を移動できます。

-   XML エディターでノードを右クリックし、選択**XML スキーマ エクスプ ローラーで表示する**します。

-   グラフ ビューで、 **XML スキーマ エクスプ ローラー**ノードをダブルクリック、またはノードを右クリックし、選択**コードの表示**します。 コンテンツ モデル ビューでは、ノードを右クリックして**コードの表示**します。

次のスクリーン ショットで開かれている XML スキーマ、 **XML スキーマ エクスプ ローラー**します。 **XML スキーマ エクスプ ローラー**ツリー ビューでスキーマ セットが表示されます。 XML エディターで現在アクティブなノードのテキスト ビューが表示されます、 **XML スキーマ エクスプ ローラー**します。

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

場合によっては、XML エディターとグラフィカルなデザイナーのコードを並べて表示すると便利です。 を同時に両方のファイルを表示するには、任意の場所の XML エディターでを右クリックして**ビュー デザイナー**します。 Visual Studio Windows メニューで、次のように選択します。**新しい水平 (または垂直) タブ グループ**します。

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>関連項目

- [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)