---
title: Python コードのパフォーマンスの測定
description: CPython ベースのインタープリターを使っているときに、Visual Studio プロファイラーを使って Python コードのパフォーマンスを調べます。
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 931bbcea67d8595ec171ef7e08756aa5b84cc2e4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062940"
---
# <a name="profile-python-code"></a>Python コードのプロファイリング

CPython ベースのインタープリターを使っている場合、Python アプリケーションをプロファイリングできます  (この機能を使うことができる Visual Studio のバージョンについては、[機能一覧のプロファイリング](overview-of-python-tools-for-visual-studio.md#matrix-profiling)を参照してください)。

## <a name="profiling-for-cpython-based-interpreters"></a>CPython ベースのインタープリターのプロファイリング

**[分析]** > **[Launch Python Profiling]\(Python プロファイリングの開始\)** メニュー コマンドでプロファイリングを開始すると、構成ダイアログが開きます。

![プロファイリング構成ダイアログ](media/profiling-start.png)

**[OK]** を選ぶと、プロファイラーが実行されてパフォーマンス レポートが表示され、アプリケーションで時間がどのように消費されたかを調べることができます。

![プロファイリング パフォーマンス レポート](media/profiling-results.png)

|   |   |
|---|---|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | Python プロファイリングのデモについては、[こちらのビデオ (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) をご覧ください (3 分 00 秒)。|

> [!Note]
> 現時点では、Visual Studio は、このレベルのフル アプリケーション プロファイリングのみをサポートしています。今後の機能に関するフィードバックをお寄せください。 このページの下部にある [**[製品のフィードバック]** ボタン](#feedback)をお使いください。

## <a name="profiling-for-ironpython"></a>IronPython のプロファイリング

IronPython は CPython ベースのインタープリターではないため、上記のプロファイリング機能は使用できません。

代わりに、ターゲット アプリケーションとして *ipy.exe* を直接起動し、適切な引数を使ってスタートアップ スクリプトを起動することにより、Visual Studio .NET のプロファイラーを使います。 すべての Python コードを確実にデバッグし、プロファイリングできるようにするには、コマンド ラインに `-X:Debug` を含めます。 この引数により、IronPython ランタイムとコードの両方で費やされた時間を含むパフォーマンス レポートが生成されます。 コードは、完全修飾名を使って識別されます。

または、IronPython には独自の組み込みプロファイリングがありますが、現在は適切なビジュアライザーがありません。 利用できるものについては、「[An IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/)」(IronPython プロファイラー) (MSDN ブログ) をご覧ください。
