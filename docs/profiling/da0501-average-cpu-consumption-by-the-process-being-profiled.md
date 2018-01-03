---
title: "DA0501: プロセスによる平均 CPU 使用量をプロファイリングしています。 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b17920bea82eff6e71176ff0493faf063d4c2161
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: プロセスによる平均 CPU 使用量をプロファイリングしています。
|||  
|-|-|  
|規則 ID|DA501|  
|カテゴリ|リソース監視|  
|プロファイル方法|すべて|  
|メッセージ|プロセスによる平均 CPU 使用量をプロファイリングしています。|  
|規則の種類|情報|  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 10 個収集する必要があります。  
  
## <a name="rule-description"></a>規則の説明  
 このメッセージにより、アプリケーションの命令の実行中にプロセッサがビジー状態になった時間がパーセントで報告されます。 プロファイリング中のプロセスがアクティブな状態にあるすべての測定間隔を通じて取得された値の平均値が、このメッセージによって報告されます。 複数のプロセッサが搭載されたコンピューターの場合、100% を超える値になる可能性があります。  
  
## <a name="how-to-use-rule-data"></a>規則データの使用方法  
 規則の値を使用して、特定のプログラムの異なるバージョンやビルドを比較したり、さまざまなテスト シナリオにおけるアプリケーションのパフォーマンスを確認したりします。