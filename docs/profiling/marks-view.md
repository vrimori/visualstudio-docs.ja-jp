---
title: "マーク ビュー | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.marks"
helpviewer_keywords: 
  - "プロファイル ツールのレポート, [マーク] ビュー"
  - "プロファイル ツール, [マーク] ビュー"
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# マーク ビュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[マーク\] ビューには、アプリケーションに挿入されたサンプリングおよび ETW イベントが表示されます。  
  
 レポートにあらかじめ設定されている既定のマークは、プログラムの開始と終了を示します。  
  
 自動的に生成されるマークの Windows カウンター データもこのビューに表示されます。  詳細については、「[方法 : Windows カウンター データを収集する](../profiling/how-to-collect-windows-counter-data.md)」を参照してください。  
  
 2 つのマークに対してフィルターを作成するには、マークを選択し、右クリックして、**\[マークにフィルターを追加\]** または **\[タイムスタンプにフィルターを追加\]** をクリックします。  
  
 次の表に、\[マーク\] ビューで使用できる列の定義を示します。  
  
 **\[マーク ID\]**  
 プロファイリング マークの一意識別子です。  
  
 **\[マーク名\]**  
 イベントの名前です。  
  
 **\[タイムスタンプ\]**  
 プロファイリングを開始してからイベントが記録されるまでの時間です。  
  
 Windows パフォーマンス カウンター データ  
 Windows パフォーマンス カウンター データが収集される場合は、その値がカウンターの名前の付いた列に表示されます。  
  
## 参照  
 [プロファイル ツール レポートの概要](../profiling/performance-report-overview.md)   
 [\<PAVE\_OVER\> 方法: プロファイリング マークを構成する](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Configure%20Profiling%20Marks.md)   
 [\<PAVE\_OVER\> 方法: プロファイラー データ ファイルにマークを挿入する](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Insert%20Marks%20in%20a%20Profiler%20Data%20File.md)   
 [方法 : Windows カウンター データを収集する](../profiling/how-to-collect-windows-counter-data.md)   
 [&#91;NIB&#93; Data Collection Control Window](http://msdn.microsoft.com/ja-jp/98d740d8-459f-4605-bf04-fb17aafaaa8f)