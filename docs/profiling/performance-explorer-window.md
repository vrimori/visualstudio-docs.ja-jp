---
title: "[パフォーマンス エクスプローラー] ウィンドウ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performanceexplorer"
  - "vs.performance.explorer"
helpviewer_keywords: 
  - "パフォーマンス ツール、パフォーマンス エクスプローラー"
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# [パフォーマンス エクスプローラー] ウィンドウ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 **\[パフォーマンス エクスプローラー\]** \(IDE\) のウィンドウが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のプロファイリング ツールを使用してパフォーマンス セッションを構成および開始することができます。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## パフォーマンス エクスプローラーのツール バー  
 **パフォーマンス エクスプローラー**のツール バーでは以下のオプションを使用できます。  
  
-   **\[パフォーマンス ウィザードの起動\]** \- パフォーマンス ウィザードを表示し、\[パフォーマンス エクスプローラー\] ウィンドウに新しいパフォーマンス セッションを追加します。  
  
-   **\[新しいパフォーマンス セッション\]** \- 空のパフォーマンス セッションを \[パフォーマンス エクスプローラー\] ウィンドウに追加します。  
  
-   **\[起動\]**\- **\[起動\]** コマンド ボタン リストでは、ターゲット アプリケーションを開始する際に、プロファイリングを即時に有効にする \(**\[プロファイルを使用して起動\]**\) ことも、プロファイリングを中断しておく \(**\[プロファイルを一時停止して起動\]**\) こともできます。  
  
-   **\[メソッド\]**\- セッションのプロファイリング方式をサンプリングにするか、インストルメンテーションにするかを指定します。  
  
-   **\[停止\]**\- ターゲット アプリケーションとプロファイラーを即時に終了します。  
  
-   **\[アタッチ\/デタッチ\]** \- **\[プロファイラーをプロセスにアタッチします\]** ダイアログ ボックスを表示し、プロファイラーをアタッチする実行中のプロセスを選択します。  
  
## \[パフォーマンス エクスプローラー\] ウィンドウ  
 **\[パフォーマンス エクスプローラー\]** ウィンドウには、1 つ以上のパフォーマンス セッションのバイナリおよびレポート データ ファイルを表示するツリー コントロールが表示されます。  
  
-   **\[\<セッション名\>\]** \- ツリー コントロールのルートには、セッションの名前が含まれます。  セッション名を右クリックし、セッション プロパティを設定するか、またはターゲット アプリケーションおよびプロファイラーを開始します。  
  
-   **\[ターゲット\]** \- セッションでプロファイリングされるバイナリの名前を表示します。  **\[ターゲット\]** を右クリックし、バイナリ、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト、または Web サイトを追加または削除します。  ターゲット名を右クリックし、個々のバイナリのプロパティを設定します。  
  
-   **\[レポート\]** \- セッションに対して生成されるプロファイラー データ ファイルの名前を表示します。  **\[レポート\]** を右クリックし、既存のレポートの追加、または 2 つのプロファイラー データ ファイルの比較を行います。  レポート名を右クリックし、プロファイラー データ ファイルをオープン、削除、またはエクスポートします。  
  
## 参照  
 [概要](../profiling/overviews-performance-tools.md)   
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [データ収集の制御](../profiling/controlling-data-collection.md)