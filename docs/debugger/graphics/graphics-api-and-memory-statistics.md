---
title: グラフィックス API とメモリの統計 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48c8ed3c8c2ebffc57ac46e987dbc37950cba0fd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-api-and-memory-statistics"></a>グラフィックス API とメモリ統計情報
<!-- VERSIONLESS -->
Visual Studio 2017 とグラフィックス API 統計サポートが強化およびメモリ統計情報ツールです。  これら 2 つのツールを使用して、さまざまなリソースの GPU のメモリ使用量と、Direct3D API の使用状況情報のさまざまな部分を表示できます。

## <a name="graphics-api-statistics"></a>グラフィックス API の統計情報
Visual Studio グラフィックス診断のグラフィックス API の統計情報を使用して、すべての Direct3D の呼び出しが行われたと各呼び出しの数を表示できます。  ウィンドウを表示するには、選択、**ビュー > API 統計**メニュー項目。

![API の統計情報](media/gfx_diag_api_statistics.png)

このツールは、DirectX の呼び出しが、気付かない可能性がありますを加えようとして、検出するまたは呼び出しを行う多くの場合に役立ちます。

として CSV で、さらに詳しい分析の Excel のように貼り付けることがコピーのすべてのデータ ウィンドウで右クリックすることができます。

## <a name="memory-statistics"></a>メモリ統計情報
このツールは、フレーム内に作成するグラフィック ドライバーは、リソースの割り当てメモリの量が表示されます。  このウィンドウを表示するには、選択、**ビュー > メモリ統計**メニュー項目。

![メモリ統計情報](media/gfx_diag_memory_statistics.png)

**GPU 割り当て**列に表示されるイベントによって使用されるメモリの量が表示されます、**イベント**列です。  [ウォッチ] アイコンを選択することもできます。 ![[ウォッチ] アイコン](media/gfx_watch.png)を表示する、[リソース履歴](graphics-event-list.md#resource-history)選択されたイベント。

API 統計ツールを使用してを右クリックをすべてコピー データ ウィンドウでとして CSV で、さらに詳しい分析の Excel のように貼り付けることができます。

## <a name="see-also"></a>関連項目  
[グラフィックス診断 (DirectX グラフィックスのデバッグ)](visual-studio-graphics-diagnostics.md)   
[リソースの履歴](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->