---
title: "[呼び出し元/呼び出し先] ビュー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.callercallee"
helpviewer_keywords: 
  - "プロファイル ツール、レポート、[呼び出し元/呼び出し先] ビュー"
  - "プロファイル ツール、[呼び出し元/呼び出し先] ビュー"
  - "パフォーマンス レポート、[呼び出し元/呼び出し先] ビュー"
  - "[呼び出し元/呼び出し先] ビュー"
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# [呼び出し元/呼び出し先] ビュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

呼び出し元\/呼び出し先ビューには、選択した関数およびその親関数と子関数のプロファイリング情報が表示されます。  呼び出し元\/呼び出し先ビューには、次の 3 つのグリッドがあります。  
  
 **\[現在の関数\]** は中央のグリッドに表示されます。このグリッドには、選択した関数のプロファイリング情報が表示されます。  値には、プロファイリング実行で収集された関数のすべての呼び出しが含まれます。  
  
 **\[現在の関数を呼び出した関数\]** は最上部のグリッドに表示されます。このグリッドには、呼び出し元 \(親\) 関数からの呼び出しによって生成された、選択した \(現在の\) 関数の値の数が表示されます。  
  
 **\[現在の関数によって呼び出された関数\]** は、下部のグリッドに表示されます。このグリッドには、子関数が現在の関数によって呼び出されたときに、選択した関数の呼び出し先 \(子\) 関数に関するプロファイリング情報が表示されます。  
  
 呼び出し元\/呼び出し先ビューに表示される列は、データの収集に使用したプロファイリング方式 \(サンプリングまたはインストルメンテーション\)、およびプロファイリング実行で .NET メモリ データを収集対象としたかどうかによって異なります。  
  
 ビューの中央部分にある \[現在の関数\] で別の関数を選択するには、レポート ビューの他の 2 つの部分に一覧表示されている関数の 1 つをダブルクリックします。  レポート ビューは自動的に更新され、この変更が反映されます。  
  
 データを並べ替えるには、列名をクリックします。  呼び出し元\/呼び出し先ビューには、さらに列を追加できます。  詳細については、「[方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)」を参照してください。  
  
## 参照  
 [呼び出し元\/呼び出し先ビュー](../profiling/caller-callee-view-sampling-data.md)   
 [呼び出し元\/呼び出し先ビュー](../profiling/caller-callee-view-instrumentation-data.md)   
 [呼び出し元\/呼び出し先ビュー \- インストルメンテーション](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [呼び出し元\/呼び出し先ビュー \- サンプリング](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [呼び出し元\/呼び出し先ビュー](../profiling/caller-callee-view-contention-data.md)