---
title: 文字列のビジュアライザーに文字列を表示 |Microsoft Docs
ms.date: 10/10/2018
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88ad69182a422d1fa1ee04eb35f973d0d1f7ea1c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968896"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visual Studio での文字列のビジュアライザーで文字列の表示

Visual Studio でデバッグする場合は、組み込みの文字列のビジュアライザーで文字列を表示できます。 文字列ビジュアライザーは、データのヒントやデバッガーのウィンドウ長すぎる文字列を示しています。 形式が正しくない文字列を識別できます。

組み込みの文字列のビジュアライザーには、プレーン テキスト、XML、HTML、および JSON が含まれています。 オプション。 WPF オブジェクトなど、他のいくつかの種類のビジュアライザーを開くことも、 **[自動変数]** または他のデバッガー ウィンドウ。

## <a name="open-a-string-visualizer"></a>文字列ビジュアライザーを開く

文字列のビジュアライザーを開くには、デバッグ中に停止する必要があります。 プレーン テキスト、XML、HTML、または JSON 文字列値、および、虫眼鏡アイコンを選択した変数にマウス![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")します。

![文字列ビジュアライザーを開く](../debugger/media/dbg-tips-string-visualizers.png "オープン文字列ビジュアライザー")

## <a name="view-string-visualizer-data"></a>文字列ビジュアライザー データの表示

文字列ビジュアライザー ウィンドウで、**式**変数または式をしているポインターを合わせると、フィールドに表示されます、**値**フィールドには、文字列値が表示されます。

空白**値**ビジュアライザーを選択したが、文字列を認識できないことを意味します。 たとえば、 **XML ビジュアライザー**は空白を示しています。**値**XML タグのない、テキスト文字列または JSON 文字列。

選択したビジュアライザーを認識できない文字列を表示するには、選択、**テキスト ビジュアライザー**します。 **テキスト ビジュアライザー**プレーン テキストが表示されます。

### <a name="view-json-string-data"></a>JSON 文字列データの表示

JSON のビジュアライザーで、次の図のように、適切な形式の JSON 文字列が表示されます。 正しくない形式の JSON には、エラー アイコン (または認識されない場合は空白) を表示可能性があります。 JSON エラーを識別するためにコピーして貼り付けます、文字列、JSON の lint ツールなど[JSLint](https://www.jslint.com/)します。

![JSON 文字列ビジュアライザー](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 文字列ビジュアライザー")

### <a name="view-xml-string-data"></a>XML の文字列データの表示

XML ビジュアライザーで、次の図のように整形式 XML 文字列が表示されます。 形式が正しくない XML は、XML タグ、または空白のない、認識されていない場合に表示します。

![XML 文字列のビジュアライザー](../debugger/media/dbg-string-visualizers-xml.png "XML 文字列のビジュアライザー")

### <a name="view-html-string-data"></a>文字列データの HTML の表示

適切な形式の HTML 文字列が表示されますかのように、次の図に示すように、ブラウザーでレンダリングします。 プレーン テキスト形式が正しくない HTML が表示されます。

![HTML 文字列ビジュアライザー](../debugger/media/dbg-string-visualizers-html.png "HTML 文字列ビジュアライザー")

## <a name="see-also"></a>関連項目

- [カスタム ビジュアライザーを作成する (C#、Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visual studio for Mac のデータの視覚化](/visualstudio/mac/data-visualizations)