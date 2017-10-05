---
title: "Visual Studio で Python コードのパフォーマンスを測定する | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: f01c42f073859e2e609123eb67cc9df8e26cef75
ms.contentlocale: ja-jp
ms.lasthandoff: 07/18/2017

---

# <a name="profiling-python-code"></a>Python コードのプロファイリング

CPython ベースのインタープリターを使っている場合、Visual Studio は Python アプリケーションのプロファイリングをサポートします。

**[分析] > [Launch Python Profiling (Python プロファイリングの開始)]** メニュー コマンドでプロファイリングを開始すると、構成ダイアログが開きます。

![プロファイリング構成ダイアログ](media/profiling-start.png)

**[OK]** を選ぶと、プロファイラーが実行されてパフォーマンス レポートが表示され、アプリケーションで時間がどのように消費されたかを調べることができます。

![プロファイリング パフォーマンス レポート](media/profiling-results.png)

概要については、次をご覧ください。

チュートリアルのデモについては、「[Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k)」(Python Tools for Visual Studio でのプロファイリング) (8 分 52 秒) のビデオをご覧ください。

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>IronPython のプロファイリング

IronPython は CPython ベースのインタープリターではないため、上記のプロファイリング機能は使用できません。

代わりに、ターゲット アプリケーションとして `ipy.exe` を直接起動し、適切な引数を使ってスタートアップ スクリプトを起動することにより、Visual Studio .NET のプロファイラーを使います。 すべての Python コードを強制的にデバッグ可能かつプロファイリング可能にするには、コマンド ラインに `-X:Debug` を含めます。 この引数により、IronPython ランタイムとコードの両方で費やされた時間を含むパフォーマンス レポートが生成されます。 コードは、完全修飾名を使って識別されます。

または、IronPython には独自の組み込みプロファイリングがありますが、現在は適切なビジュアライザーがありません。 利用できるものについては、「[An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx)」(IronPython プロファイラー) (MSDN ブログ) をご覧ください。
