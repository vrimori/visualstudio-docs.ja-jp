---
title: "スレッドおよびプロセスの同時実行データの収集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "同時実行プロファイル方法"
  - "プロファイリング ツール, 同時実行メソッド"
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# スレッドおよびプロセスの同時実行データの収集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のプロファイリング ツールの同時実行プロファイル方法は、リソースへのアクセスで待機がプロファイリング対象のアプリケーションで関数をするすべての同期イベントに関する情報を含むリソース競合データを収集できるようになります。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 同時実行プロファイル方法は、次のいずれかの手順で指定できます。  
  
-   プロファイル ウィザードの最初のページで、**\[並行性\]** をクリックします  
  
-   パフォーマンス セッションのプロパティ ダイアログ ボックスの **\[全般\]** ページで、**\[並行性\]** をクリックします。  
  
-   **パフォーマンス エクスプローラー**のツール バーで、**\[メソッド\]** ボックスの一覧の **\[同時実行\]** をクリックします。  
  
## 一般的なタスク  
 パフォーマンス セッションの *Performance Session***\[プロパティ ページ\]** ダイアログ ボックスで追加のオプションを指定できます。  このダイアログ ボックスを開くには、次の操作を行います。  
  
-   **パフォーマンス エクスプローラー**で、パフォーマンス セッション名を右クリックし、**\[プロパティ\]** をクリックします。  
  
 次の表のタスクは、同時実行メソッドを使用したプロファイリングを実行するときに *Performance Session***\[プロパティ ページ\]** ダイアログ ボックスで指定できるオプションについて説明します。  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**\[全般\]** ページで、生成されるプロファイル データ \(.vsp\) ファイルの名前付けの詳細を指定します。|-   [方法: プロファイル データ ファイル名のオプションを設定する](../profiling/how-to-set-performance-data-file-name-options.md)|  
|コード ソリューション内に複数の .exe プロジェクトがある場合は、**\[起動\]** ページで、開始するアプリケーションを指定します。|-   [方法 : 開始するバイナリを指定する](../profiling/how-to-specify-the-binary-to-start.md)|  
|**\[階層の相互作用\]** ページで、プロファイリング実行に ADO.NET 呼び出しデータを追加します。|-   [階層相互作用データの収集](../profiling/collecting-tier-interaction-data.md)|  
|**\[Windows カウンター\]** ページで、プロファイル データにマークとして追加するオペレーティング システムのパフォーマンス カウンターを 1 つ以上指定します。|-   [方法 : Windows カウンター データを収集する](../profiling/how-to-collect-windows-counter-data.md)|  
|アプリケーション モジュールが複数バージョンの .NET Framework ランタイムを使用する場合、**\[詳細\]** ページで、プロファイルする .NET Framework ランタイム バージョンを指定します。  既定では、最初に読み込まれたバージョンがプロファイリングされます。|-   [方法: side\-by\-side 実行でプロファイリングするように .NET Framework ランタイムを指定する](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|