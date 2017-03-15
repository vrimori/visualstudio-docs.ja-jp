---
title: "DA0008: 少数のサンプルしか収集されていません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DATooFewSamples"
  - "vs.performance.8"
  - "vs.performance.DA0008"
  - "vs.performance.rules.DA0008"
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# DA0008: 少数のサンプルしか収集されていません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0008|  
|分類|プロファイリング ツールの使用|  
|プロファイル方法|サンプリング|  
|メッセージ|少数のサンプルしか収集されていません。  収集されるサンプル数を増やすには、実行時間を長くするか、サンプリング速度を上げてください。|  
|規則の種類|情報|  
  
## 原因  
 プロファイリング実行で少数のサンプルしか収集されませんでした。  
  
## 規則の説明  
 サンプリング メソッドを使用するときは、実際のプログラムの動作を表すようなデータを確実に得るために、統計的に有意な数のサンプルを収集する必要があります。  サンプリング エラーを最小限に抑えるには、プログラム命令の実行動作のサンプルを少なくとも 1000 個収集するようにしてください。  十分なサンプルを収集しない場合、プロファイル データを分析したときに誤った結果が得られる可能性があります。  
  
## 違反の修正方法  
 統計的に有意な結果を得るために、プロファイリングするアプリケーションの実行時間を長くするか、サンプリング速度を上げることを検討してください。  Visual Studio IDE でサンプル速度を変更する方法については、「[方法 : サンプリング イベントを選択する](../Topic/How%20to:%20Choose%20Sampling%20Events.md)」を参照してください。  コマンド ラインからプロファイリング ツールを使用してサンプル速度を変更する方法の詳細については、[VSPerfCmd](../profiling/vsperfcmd.md) リファレンスの「[Timer](../profiling/timer.md)」を参照してください。