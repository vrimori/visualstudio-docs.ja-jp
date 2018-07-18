---
title: '方法: ビューと XML エディターを切り替える'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b0eb90f2ead313ce94d609d71385b595f3e964b
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
ms.locfileid: "34477731"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>方法: ビューと XML エディターを切り替える

このトピックでは、XML スキーマ デザイナー (XSD デザイナー) のビューと XML エディターを切り替える方法について説明します。 この例では、[購買発注書スキーマ](../xml-tools/sample-xsd-file-simple-schema.md)です。

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>ビューと XML エディターを切り替えるには

1.  作成し、新しい XML スキーマ ファイルを編集して、手順を[する方法: を作成し、XSD スキーマ ファイルを編集](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)です。

2.  XML エディターから XML スキーマ デザイナーに切り替え、XML エディターで任意の場所を右クリックし、選択**ビュー デザイナー**です。

3.  透かしを使用してグラフ ビューに切り替えるをクリックして、**グラフ ビューを使用して、ノード間のリレーションシップを参照してください**スタート ビューにリンクします。

4.  ドラッグ、`USAddress`ノードから、 **XML スキーマ エクスプ ローラー**グラフ ビューにします。 右クリックし、`USAddress`クリックし、グラフ ビューでノード**コンテンツ モデル ビューに表示する**コンテキスト メニュー。

     `USAddress` ノードの詳細を示したコンテンツ モデル ビューが表示されます。

5.  ツールバーを使用してコンテンツ モデル ビューからスタート ビューに切り替えるをクリックして、**スタート ビュー** XSD ツールバーのボタンをクリックします。

6.  ビューに切り替える、ホットキーを使用して、キーを押します**Ctrl**+**1** 、スタート ビューの**Ctrl**+**2**グラフ ビューのおよび**ctrl キーを押し**+**3**コンテンツ モデル ビューにします。

7.  移動する XML エディターに、コンテンツ モデル ビューからノードを右クリックし、選択**コードの表示**コンテキスト メニュー。