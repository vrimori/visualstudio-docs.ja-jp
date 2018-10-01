---
title: 'DA0026: 過剰なカーネル CPU 処理時間。 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29eda10403e2d09f5a1bdf67911e1f2ae58bd9f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537195"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: 過剰なカーネル CPU 処理時間。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[da 0026: 過剰なカーネル CPU 処理時間](https://docs.microsoft.com/visualstudio/profiling/da0026-excessive-kernel-cpu-time-processing)します。  
  
規則 Id |TODO |  
|カテゴリ |プロファイリング ツールの使用 |  
|プロファイル方法 |サンプリング |  
|メッセージ |比較的高いカーネル モード CPU 時間の量が測定されました。 SysCall サンプリングを有効にした原因の調査を検討してください |。  
|規則の種類 |情報 |  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 10 個収集する必要があります。  
  
## <a name="cause"></a>原因  
 カーネル モードで実行された CPU 時間の割合が、ユーザー モードで費やされた時間数を超えました。 カーネル モードの実行時間が長い原因を判断するために、プロファイリングを再度実行し、システム コール (syscalls) の数をサンプリングすることを検討してください。  
  
## <a name="rule-description"></a>規則の説明  
 カーネル モードでの実行中にアプリケーションの処理時間が比較的長くなっている場合は、さらに調査が必要になることがあります。 ユーザー モードのアプリケーションは、I/O 操作の実行、スレッドまたはプロセスの同期プリミティブの待機、またはシステム コールを実行するために、カーネル モードに遷移します。 システム コールに基づいてサンプルの呼び出し履歴を収集するオプションを選択する際に、アプリケーションが実行するシステム コールの種類とそのシステム コールを処理する関数を調べることができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 アプリケーションが実行するシステム コールを調べるには、プロファイルを再度実行し、システム コールに基づいてサンプルを収集するオプションを選択します。 IDE 内でプロファイリング ツールを実行する場合の詳細については、「[方法 : サンプリング イベントを選択する](../profiling/how-to-choose-sampling-events.md)」を参照してください。 コマンド ラインからプロファイリング ツールを実行する場合の詳細については、コマンド ライン プロファイリング ツール リファレンスのトピック、「[VSPerfCmd](../profiling/vsperfcmd.md)」の「**サンプリング間隔オプション**」のセクションを参照してください。



