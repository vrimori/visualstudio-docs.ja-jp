---
title: "リソース監視のパフォーマンス規則 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 32ddf4774de92a24a5839f320d09eb61898c69d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="resource-monitoring-performance-rules"></a>リソース監視のパフォーマンス規則
リソース監視カテゴリのパフォーマンス メッセージでは、アプリケーションのパフォーマンスに関する追加データが提供されます。 このデータを使用してパフォーマンスの問題を分析できます。 これらの規則は情報を提供するためのものであり、プロファイル実行ごとに報告されます。  
  
|||  
|-|-|  
|[DA0501: プロセスによる平均 CPU 使用量をプロファイリングしています。](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|このメッセージにより、アプリケーションの命令の実行中にプロセッサがビジー状態になった時間がパーセントで報告されます。 プロファイリング中のプロセスがアクティブな状態にあるすべての測定間隔を通じて取得された値の平均値が、このメッセージによって報告されます。|  
|[DA0502: プロセスによる最大 CPU 使用量をプロファイリングしています](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|このメッセージにより、アプリケーションの命令の実行中にプロセッサがビジー状態になった最大時間がパーセントで報告されます。 プロファイリング中のプロセスがアクティブな状態にあるすべての測定間隔を通じて取得された値のうち、最も大きな値がこのメッセージによって報告されます。|  
|[DA0503: プロセスのワーキング セット平均バイト数がプロファイリングされています](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|このメッセージにより、プロファイルがアクティブな状態にあったときにプロセスが使用していた物理メモリ量の平均がバイト単位で報告されます。 この物理メモリの大きさはワーキング セットと呼ばれます。|  
|[DA0504: プロセスのワーキング セット最大バイト数がプロファイリングされています](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|このメッセージにより、プロファイルがアクティブな状態にあったときにプロセスが使用していた物理メモリの最大量がバイト単位で報告されます。|  
|[DA0505: プロセスに割り当てられた平均プライベート バイト数がプロファイリングされています](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|このメッセージにより、プロファイルがアクティブな状態にあったときにプロセスによって割り当てられた仮想メモリ量の平均がバイト単位で報告されます。 この仮想メモリの大きさは*プライベート バイト*と呼ばれます。 プライベート バイトは、プロセス内部で実行中のスレッドからのみアクセスできるプロセスによって割り当てられた仮想メモリの位置を表します。|  
|[DA0506: プロセスに割り当てられた最大プライベート バイト数がプロファイリングされています](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|このメッセージにより、プロファイルがアクティブな状態にあったときにプロセスによって割り当てられた仮想メモリの最大量がプライベート バイト単位で報告されます。|