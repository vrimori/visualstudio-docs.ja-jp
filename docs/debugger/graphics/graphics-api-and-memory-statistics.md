---
title: グラフィックス API とメモリの統計情報 |Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0c1ed6e2fdd461b0fdf502c01089aeafd9a87cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925631"
---
# <a name="graphics-api-and-memory-statistics"></a>グラフィックス API とメモリの統計情報
<!-- VERSIONLESS --> Visual Studio 2017 およびそれ以降は、グラフィックス API 統計情報とメモリの統計情報のツールをサポートします。  これら 2 つのツールを使用して、さまざまなリソースの GPU メモリ使用量と、Direct3D API 使用量情報のさまざまな部分を表示できます。

## <a name="graphics-api-statistics"></a>グラフィックス API 統計情報
Visual Studio グラフィックス診断でグラフィックス API 統計情報を使用して、すべての変更を行った Direct3D の呼び出しと各呼び出しの数を表示できます。  ウィンドウを表示するには、選択、**ビュー > API 統計情報**メニュー項目。

![API 統計情報](media/gfx_diag_api_statistics.png)

このツールは、検出気付いていないする DirectX の呼び出しを行っている、または頻繁に行っている呼び出しに役立ちます。

CSV で、さらに詳しい分析の Excel のようなものに貼り付けることができるとしてコピーすべてのデータ ウィンドウで右クリックできます。

## <a name="memory-statistics"></a>メモリ統計情報
このツールは、フレームで作成したリソースのグラフィック ドライバーを割り当てるメモリの量が表示されます。  このウィンドウを表示するには、選択、**ビュー > メモリ統計情報**メニュー項目。

![メモリ統計情報](media/gfx_diag_memory_statistics.png)

**GPU 割り当て**列に表示されるイベントによって使用されるメモリ量が表示されます、**イベント**列。  [ウォッチ] アイコンを選択することもできます。![ウォッチ アイコン](media/gfx_watch.png)を表示する、[リソース履歴](graphics-event-list.md#resource-history)選択されたイベント。

API 統計情報ツールと同様を右クリックしてコピーすべてのデータをウィンドウとして CSV で、さらに詳しい分析の Excel のように貼り付けることができます。

## <a name="see-also"></a>「  
[グラフィックス診断 (DirectX グラフィックスのデバッグ)](visual-studio-graphics-diagnostics.md)   
[リソース履歴](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->