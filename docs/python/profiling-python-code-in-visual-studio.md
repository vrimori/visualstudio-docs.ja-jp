---
title: "Visual Studio で Python コードのパフォーマンスを測定する | Microsoft Docs"
description: "CPython ベースのインタープリターを使っているときに、Visual Studio プロファイラーを使って Python コードのパフォーマンスを調べる方法を説明します。"
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 0faae917aba237a85c6a01743d89cf66adf06296
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="profiling-python-code"></a>Python コードのプロファイリング

CPython ベースのインタープリターを使っている場合、Python アプリケーションをプロファイリングできます  (この機能を使うことができる Visual Studio のバージョンについては、[機能一覧のプロファイリング](overview-of-python-tools-for-visual-studio.md#matrix-profiling)を参照してください)。

**[分析] > [Launch Python Profiling (Python プロファイリングの開始)]** メニュー コマンドでプロファイリングを開始すると、構成ダイアログが開きます。

![プロファイリング構成ダイアログ](media/profiling-start.png)

**[OK]** を選ぶと、プロファイラーが実行されてパフォーマンス レポートが表示され、アプリケーションで時間がどのように消費されたかを調べることができます。

![プロファイリング パフォーマンス レポート](media/profiling-results.png)

|   |   |
|---|---|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | Python プロファイリングのデモについては、[こちらのビデオ (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) をご覧ください (3 分 00 秒)。|

## <a name="profiling-for-ironpython"></a>IronPython のプロファイリング

IronPython は CPython ベースのインタープリターではないため、上記のプロファイリング機能は使用できません。

代わりに、ターゲット アプリケーションとして `ipy.exe` を直接起動し、適切な引数を使ってスタートアップ スクリプトを起動することにより、Visual Studio .NET のプロファイラーを使います。 すべての Python コードを確実にデバッグし、プロファイリングできるようにするには、コマンド ラインに `-X:Debug` を含めます。 この引数により、IronPython ランタイムとコードの両方で費やされた時間を含むパフォーマンス レポートが生成されます。 コードは、完全修飾名を使って識別されます。

または、IronPython には独自の組み込みプロファイリングがありますが、現在は適切なビジュアライザーがありません。 利用できるものについては、「[An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx)」(IronPython プロファイラー) (MSDN ブログ) をご覧ください。