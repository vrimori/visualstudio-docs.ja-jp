---
title: "コール ツリー ビュー | Microsoft Docs"
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
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "[呼び出しツリー] ビュー"
  - "パフォーマンス レポート, [呼び出しツリー] ビュー"
  - "プロファイル ツールのレポート, [呼び出しツリー] ビュー"
  - "プロファイル ツール, [呼び出しツリー] ビュー"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# コール ツリー ビュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[コール ツリー\] ビューには、プロファイリングされるアプリケーションで走査された関数の実行パスが表示されます。  ツリーのルートは、アプリケーションまたはコンポーネントへのエントリ ポイントです。  各関数ノードは、呼び出したすべての関数と、その関数呼び出しに関するパフォーマンス データを表示します。  
  
 \[コール ツリー\] ビューでは、最も時間を消費した関数または最も頻繁にサンプリングされた関数の実行パスを展開および強調表示することもできます。  最もパフォーマンスに負荷のかかるパスを表示するには、関数を右クリックし、**\[ホット パスの展開\]** をクリックします。  
  
 プロファイリング実行の各プロセスは、ルート ノードとして表示されます。  コール ツリー ビューの開始ノードを設定するには、開始ノードとして設定するノードを右クリックし、**\[ルートの設定\]** をクリックします。  
  
 ルート ノードを設定すると、選択したノードのサブツリーを除く他のすべてのエントリはビューから除外されます。  ルート ノードをリセットして、表示していたノードに戻すことができます。  \[コール ツリー\] ビューのウィンドウで右クリックし、**\[ルートのリセット\]** をクリックします。  
  
 \[コール ツリー\] ビューは、列を追加または削除してカスタマイズできます。  **列名のタイトル バー**を右クリックし、**\[列の追加と削除\]** をクリックします。  
  
 \[コール ツリー\] ビューは、表示するデータの数を制限して、ノイズを除去するように構成できます。  ノイズ除去を行うことで、ビューでパフォーマンスの問題を発見しやすくなります。  パフォーマンスの問題が特定しやすくなると、分析も容易になります。  詳細については、「[方法: レポート ビューでノイズ除去を設定する](../profiling/how-to-configure-noise-reduction-in-report-views.md)」を参照してください。  
  
> [!NOTE]
>  ノイズ除去が有効になっているときに警告を表示するように構成すると、レポートに情報バーが表示されます。  
  
 コール ツリー ビューでの列の定義の詳細については、次を参照してください。  
  
 [コール ツリー ビュー](../profiling/call-tree-view-sampling-data.md)  
  
 [コール ツリー ビュー](../profiling/call-tree-view-instrumentation-data.md)  
  
 [コール ツリー ビュー \- サンプリング](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [コール ツリー ビュー](../profiling/call-tree-view-contention-data.md)  
  
## 参照  
 [プロファイル ツールのレポート ビュー](../profiling/performance-report-views.md)   
 [インストルメンテーション データ値について](../profiling/understanding-instrumentation-data-values.md)   
 [サンプリング データ値について](../profiling/understanding-sampling-data-values.md)