---
title: 'DA0008: 少数のサンプルしか収集されていません | Microsoft Docs'
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
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6e294c03f958259f26938865a3e26c6fb7669d6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289810"
---
# <a name="da0008-few-samples-collected"></a>DA0008: 少数のサンプルしか収集されていません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0008 |  
|カテゴリ |プロファイリング ツールの使用 |  
|プロファイル方法 |サンプリング |  
|メッセージ |サンプルをいくつかのみが収集されませんでした。 多くの結果の長い実行か、サンプル速度を検討してください |。  
|規則の種類 |情報 |  
  
## <a name="cause"></a>原因  
 プロファイリング実行で少数のサンプルしか収集されませんでした。  
  
## <a name="rule-description"></a>規則の説明  
 サンプリング メソッドを使用するときは、実際のプログラムの動作を表すようなデータを確実に得るために、統計的に有意な数のサンプルを収集する必要があります。 サンプリング エラーを最小限に抑えるには、プログラム命令の実行動作のサンプルを少なくとも 1000 個収集するようにしてください。 十分なサンプルを収集しない場合、プロファイル データを分析したときに誤った結果が得られる可能性があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 統計的に有意な結果を得るために、プロファイリングするアプリケーションの実行時間を長くするか、サンプリング速度を上げることを検討してください。 Visual Studio IDE でサンプル速度を変更する方法については、「[方法 : サンプリング イベントを選択する](../profiling/how-to-choose-sampling-events.md)」を参照してください。 コマンド ラインからプロファイリング ツールを使用してサンプル速度を変更する方法の詳細については、「[VSPerfCmd](../profiling/vsperfcmd.md)」リファレンスの「[Timer](../profiling/timer.md)」を参照してください。



