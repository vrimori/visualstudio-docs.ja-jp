---
title: 'DA0501: プロセスによる平均 CPU 使用量をプロファイリングしています。 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e2a270195a4d3689b2a5756c4633654bd3f06ae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194214"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: プロセスによる平均 CPU 使用量をプロファイリングしています。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA501 |  
|カテゴリ |リソースの監視 |  
|プロファイル方法 |すべて |  
|メッセージ |プロファイリング中のプロセスによる CPU 使用量の平均です |。  
|規則の種類 |情報 |  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 10 個収集する必要があります。  
  
## <a name="rule-description"></a>規則の説明  
 このメッセージにより、アプリケーションの命令の実行中にプロセッサがビジー状態になった時間がパーセントで報告されます。 プロファイリング中のプロセスがアクティブな状態にあるすべての測定間隔を通じて取得された値の平均値が、このメッセージによって報告されます。 複数のプロセッサが搭載されたコンピューターの場合、100% を超える値になる可能性があります。  
  
## <a name="how-to-use-rule-data"></a>規則データの使用方法  
 規則の値を使用して、特定のプログラムの異なるバージョンやビルドを比較したり、さまざまなテスト シナリオにおけるアプリケーションのパフォーマンスを確認したりします。



