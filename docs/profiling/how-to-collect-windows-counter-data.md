---
title: "方法 : Windows カウンター データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.syscounter"
  - "vs.performance.property.wincounter"
helpviewer_keywords: 
  - "Windows カウンター"
  - "パフォーマンス ツール、使用 (Windows カウンターを)"
  - "プロファイル ツール、使用 (Windows カウンターを)"
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : Windows カウンター データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows カウンターは、プロファイル中に一定間隔で収集できるシステム パフォーマンス カウンターです。  プロファイル ツール レポートのマーク ビューでは、データ収集の間隔ごとに **\[AutoMark\]** のラベルが行に付けられます。  この行には、その間隔でのパフォーマンス カウンター値を示す列が含まれます。  2 個の具体的なマーク間の時間を分析するには、マークを選択して右クリックし、ショートカット メニューの  **\[ マーク\]** \-\> を **\[フィルター方法\]** を選択します。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。  Windows ストア アプリにも新しい収集手法が必要です。  「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
### Windows カウンター データを収集するには  
  
1.  パフォーマンス エクスプローラーで、Windows カウンターを構成するセッションを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ ページ\]** で、**\[Windows カウンター\]** をクリックします。  
  
3.  **\[Windows カウンターの収集\]** チェック ボックスをオンにします。  
  
4.  **\[収集間隔 \(ミリ秒\)\]** ボックスに、間隔を入力します。  
  
5.  **\[カウンター カテゴリ\]** ボックスの一覧で、カテゴリを選択します。  
  
6.  **\[インスタンス\]** ボックスの一覧で、インスタンスを選択します。  
  
7.  アプリケーションをプロファイルするときに使用するカウンターを選択します。  
  
8.  **\[適用\]** をクリックします。  
  
## 参照  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [パフォーマンス セッションのプロパティ](../profiling/performance-session-properties.md)   
 [CPU カウンターと Windows カウンター](../profiling/cpu-and-windows-counters.md)