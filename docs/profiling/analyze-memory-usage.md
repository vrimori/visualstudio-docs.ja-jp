---
title: Visual Studio でメモリ使用量を分析する | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cee40dd1dab8c3a9d9b57b84e6e299651bc5fc8
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "42626569"
---
# <a name="analyze-memory-usage"></a>メモリ使用量の分析
デバッガーに統合された**メモリ使用量**診断ツールを使って、メモリ リークおよび非効率的なメモリ使用を見つけます。 メモリ使用量ツールを使用すると、マネージド メモリ ヒープ、およびネイティブ メモリ ヒープの 1 つまたは複数の *スナップショット* を取得できます。 .NET アプリ、ネイティブ アプリ、または混在モード (.NET とネイティブ) アプリのスナップショットを収集できます。  
  
-   単一のスナップショットを分析することにより、オブジェクト型のメモリ使用に対する相対的な影響を理解し、アプリ内でメモリが効率的に使用されていないコードを検出することができます。  
  
-   アプリの 2 つのスナップショットを比較 (diff) することにより、コード内で時間の経過に伴ってメモリ使用量が増加している箇所を検出することもできます。  

方法については、「[メモリ使用量の分析](../profiling/memory-usage.md)」チュートリアルをご覧ください。 デバッガーをアタッチしないでメモリ使用量を分析するには、「[デバッガーなしのメモリ使用量](memory-usage-without-debugging2.md)」を参照してください。

Windows 7 以降ではデバッガーなしでプロファイル ツールを使用することができます。 Windows 8 以降では、デバッガーを使用してプロファイル ツールを実行する必要があります (**[診断ツール]** ウィンドウ)。
  
## <a name="blogs-and-videos"></a>ブログとビデオ  

|         |         |
|---------|---------|
|  ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る")  |    診断ツールの使い方については、Visual Studio 2017 でのメモリ使用量と CPU 使用量を分析する方法がわかる[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171)をご覧ください。 |

 [デバッグ中に CPU とメモリを分析する](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ ブログ: Visual C++ 2015 でのメモリ プロファイル](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>関連項目
 [Visual Studio のプロファイル](../profiling/index.md)  
 [プロファイル ツールの概要](../profiling/profiling-feature-tour.md)