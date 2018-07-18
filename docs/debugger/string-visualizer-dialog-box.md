---
title: 文字列のビジュアライザーに文字列を表示 |Microsoft ドキュメント
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
ms.openlocfilehash: a3a0575b02422bf83dd560d3eae5724b0a50d3f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476976"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visual Studio での文字列のビジュアライザーで文字列を表示します。
デバッグしている間がデータ ヒントまたはデバッガー ウィンドウに表示するのには長すぎる文字列を表示する文字列のビジュアライザーを開くことができます。 多くのシナリオでビジュアライザーに役立つことが正しくない形式の文字列を識別します。

標準的な組み込みの文字列のビジュアライザーには、プレーン テキスト、XML、HTML、および JSON が含まれます。 デバッガーで表示されている WPF オブジェクトなどの他のいくつかの種類の windows と同様に、 **[自動変数]** ウィンドウで、ビジュアライザーを開くこともできます。

## <a name="open-a-string-visualizer"></a>文字列ビジュアライザーを開く

プレーン テキスト、XML、HTML、または JSON 文字列を表示するには、虫眼鏡アイコンをクリックして![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")文字列値を含む変数の上にマウス中にします。 虫眼鏡アイコンを表示するには、デバッガーで一時停止している必要があります。

![文字列ビジュアライザーを開く](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>文字列データの表示

**式**string ビジュアライザー内のフィールドは、デバッガーで、現在の変数またはグループに置かれている式を示しています。 します。

**値**フィールドは文字列値を表示します。 テキスト ビジュアライザーでは、プレーン テキストを示します。

空白**値**特定のビジュアライザーが文字列型を認識できないことを示します。 たとえば、XML ビジュアライザーは、空白を示しています。**値**XML タグのない) 簡単なテキスト文字列または JSON 形式の文字列にします。 ビジュアライザーで、認識できない文字列を表示する必要がある場合は、テキスト ビジュアライザーを使用できます。

### <a name="view-json-string-data"></a>JSON 文字列データの表示

適切な形式の JSON 文字列は、JSON のビジュアライザーに次の図のように表示されます。 正しくない形式の JSON には、エラー アイコン (または認識されていない場合は空白) を表示可能性があります。

![JSON 文字列ビジュアライザー](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 文字列ビジュアライザー")

### <a name="view-xml-string-data"></a>XML 文字列データの表示

整形式 XML 文字列は、XML ビジュアライザーで次の図のように表示されます。 誤った形式の XML は、XML タグ (または認識されていない場合は空白) せず表示可能性があります。

![XML 文字列のビジュアライザー](../debugger/media/dbg-string-visualizers-xml.png "XML 文字列ビジュアライザー")

### <a name="view-html-string-data"></a>HTML の文字列データの表示

適切な形式の HTML 文字列が表示されるかどうか、ブラウザーで、文字列が表示されます。 次の図に示すようにビューに似ていますが表示されます。 不正な HTML がプレーン テキストで表示します。

![HTML 文字列ビジュアライザー](../debugger/media/dbg-string-visualizers-html.png "HTML 文字列ビジュアライザー")

## <a name="see-also"></a>関連項目  
 [カスタム ビジュアライザー (c#、Visual Basic) を作成します。](../debugger/create-custom-visualizers-of-data.md)