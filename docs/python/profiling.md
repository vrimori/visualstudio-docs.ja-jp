---
title: "Visual Studio で Python コードのパフォーマンスを測定する | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 8d52ad780eb8aa29132626644d581d3a5b6e66b4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---

# <a name="profiling-python-code"></a>Python コードのプロファイリング

CPython ベースのインタープリターを使っている場合、Visual Studio は Python アプリケーションのプロファイリングをサポートします。

**[分析] > [Launch Python Profiling (Python プロファイリングの開始)]** メニュー コマンドでプロファイリングを開始すると、構成ダイアログが開きます。

![プロファイリング構成ダイアログ](~/python/media/profiling-start.png)

**[OK]** を選ぶと、プロファイラーが実行されてパフォーマンス レポートが表示され、アプリケーションで時間がどのように消費されたかを調べることができます。

![プロファイリング パフォーマンス レポート](~/python/media/profiling-results.png)

概要については、次をご覧ください。

チュートリアルのデモについては、「[Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k)」(Python Tools for Visual Studio でのプロファイリング) (8 分 52 秒) のビデオをご覧ください。

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>IronPython のプロファイリング

IronPython は CPython ベースのインタープリターではないため、上記のプロファイリング機能は使用できません。

代わりに、ターゲット アプリケーションとして `ipy.exe` を直接起動し、適切な引数を使ってスタートアップ スクリプトを起動することにより、Visual Studio .NET のプロファイラーを使います。 すべての Python コードを強制的にデバッグ可能かつプロファイリング可能にするには、コマンド ラインに `-X:Debug` を含めます。 これにより、パフォーマンス レポートには IronPython ランタイムとコードの両方で費やされた時間が含まれます。 コードは、完全修飾名を使って識別されます。

または、IronPython には独自の組み込みプロファイリングがありますが、現在は適切なビジュアライザーがありません。 利用できるものについては、「[An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx)」(IronPython プロファイラー) (MSDN ブログ) をご覧ください。
