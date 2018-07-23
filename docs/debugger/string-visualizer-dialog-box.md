---
title: 文字列のビジュアライザーに文字列を表示 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6e4519a85659b36e5cf6baebaadd1d1c626f1a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151036"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visual Studio での文字列のビジュアライザーで文字列の表示
をデバッグするときに、データ ヒントやデバッガー ウィンドウに表示するには長すぎる文字列の表示を文字列ビジュアライザーを開くことができます。 多くのシナリオでは、ビジュアライザーは、形式が正しくない文字列を識別するヘルプことができます。

標準的な組み込みの文字列のビジュアライザーには、プレーン テキスト、XML、HTML、および JSON が含まれます。 Windows などのデバッガーで表示されている WPF オブジェクトなど、他のいくつかの種類、 **[自動変数]** ウィンドウで、ビジュアライザーを開くこともできます。

## <a name="open-a-string-visualizer"></a>文字列ビジュアライザーを開く

プレーン テキスト、XML、HTML、または JSON 文字列を表示するには、虫眼鏡アイコンをクリックします。 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")文字列値を含む変数を合わせたとき。 虫眼鏡アイコンを表示する、デバッガーで一時停止している必要があります。

![文字列ビジュアライザーを開く](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>文字列データの表示

**式**文字列ビジュアライザー内のフィールドがデバッガーで、現在の変数または式をマウスでポイントを示しています。

**値**フィールドには、文字列値が表示されます。 テキスト ビジュアライザーには、プレーン テキストが表示されます。

空白**値**特定ビジュアライザーが文字列型を認識できないことを示します。 たとえば、XML ビジュアライザーは、空白を示しています。**値**の XML タグのない) の単純なテキスト文字列または JSON 形式の文字列。 ビジュアライザーで、認識できない文字列を表示する必要がある場合は、テキスト ビジュアライザーを使用します。

### <a name="view-json-string-data"></a>JSON 文字列データの表示

適切な形式の JSON 文字列は、JSON のビジュアライザーで、次の図のように表示されます。 正しくない形式の JSON には、エラー アイコン (または認識されない場合は空白) を表示可能性があります。 エラー アイコンを表示する場合は、コピーしてなど、JSON の lint 処理ツールに、JSON 文字列を貼り付けます[JSLint](https://www.jslint.com/) JSON エラーを識別します。

![JSON 文字列ビジュアライザー](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 文字列ビジュアライザー")

### <a name="view-xml-string-data"></a>XML の文字列データの表示

整形式 XML 文字列は、XML ビジュアライザーで、次の図のように表示されます。 XML タグ (または認識されない場合は空白です) がない形式が正しくない XML が表示されます。

![XML 文字列のビジュアライザー](../debugger/media/dbg-string-visualizers-xml.png "XML 文字列のビジュアライザー")

### <a name="view-html-string-data"></a>文字列データの HTML の表示

適切な形式の HTML 文字列が表示されるかどうか、文字列は、ブラウザーで表示されます。 次の図に示すようにビューに似ていますが表示されます。 プレーン テキスト形式が正しくない HTML が表示されます。

![HTML 文字列ビジュアライザー](../debugger/media/dbg-string-visualizers-html.png "HTML 文字列ビジュアライザー")

## <a name="see-also"></a>関連項目  
 [(C#、Visual Basic) のカスタム ビジュアライザーを作成します。](../debugger/create-custom-visualizers-of-data.md)