---
title: "プロファイリング ツールでのデータ収集の制御 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "高度なタスク (プロファイル ツール用の)"
  - "プロファイル ツール, 高度なタスク"
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# プロファイリング ツールでのデータ収集の制御
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールを使用すると、パフォーマンス セッション中のプロファイリング データを収集するタイミングを制御し、プロファイリングする関数を指定することができます。  ここでは、**\[パフォーマンス エクスプローラー\]** ウィンドウおよび **\[データ収集コントロール\]** ウィンドウからデータ収集を開始および停止する方法と、プロファイリング データを収集するオブジェクトを制限する方法について説明します。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**プロファイリングの開始および停止:** アプリケーションのプロファイリングは、アプリケーションの起動時または既に実行中のプロセスにプロファイラーをアタッチすることで開始できます。  ターゲット アプリケーションの実行中は、データ収集を一時停止したり、再開することができます。  プロファイル セッションを終了するには、ターゲット アプリケーションを終了するか、プロファイラーを実行中のプロセスからデタッチします。|-   [方法 : プロファイリングの開始と終了](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [方法 : 実行中のプロセスにプロファイラーをアタッチする\/実行中のプロセスからプロファイラーをデタッチする](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [方法 : プロファイリングを一時停止および再開する](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)|  
|**収集データを制限するようにインストルメンテーション プロファイリングを構成:** パフォーマンス セッションの構成プロパティを使用して、インストルメンテーション メソッドを使用するプロファイリング実行で収集されるデータを制限できます。  特定の .dll ファイル、名前空間、クラス、および関数を含めたり、除外することができます。  さらに、指定したサイズのしきい値に満たない関数を除外することもできます。|-   [方法 : インストルメンテーションを特定の DLL に制限する](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [方法 : インストルメンテーションを特定の関数に制限する](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [方法 : インストルメンテーションで短い関数を除外または含める](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)|  
  
## 関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)  
  
## 参照  
 [プロファイリング ツールの使用](../profiling/performance-explorer.md)