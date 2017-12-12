---
title: "方法 : Windows カウンター データを収集する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5b16cf6260932f11c9d4fd33f2eb5662327355a
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-collect-windows-counter-data"></a>方法 : Windows カウンター データを収集する
Windows カウンターは、プロファイル中に一定間隔で収集できるシステム パフォーマンス カウンターです。 プロファイリング ツール レポートのマーク ビューでは、データ収集の間隔ごとに **[AutoMark]** のラベルが行に付けられます。 この行には、その間隔でのパフォーマンス カウンター値を示す列が含まれます。 2 個の具体的なマーク間の時間を分析するには、マークを選択して右クリックし、ショートカット メニューの **[フィルター方法]** ->  **[マーク]** を選択します。  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 UWP アプリにも新しい収集手法が必要です。 ｢[Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール)」をご覧ください。  
  
### <a name="to-collect-windows-counter-data"></a>Windows カウンター データを収集するには  
  
1.  パフォーマンス エクスプローラーで、Windows カウンターを構成するセッションを右クリックし、**[プロパティ]** を選択します。  
  
2.  **[プロパティ] ページ**で、**[Windows カウンター]** をクリックします。  
  
3.  **[Windows カウンターの収集]** チェックボックスをオンにします。  
  
4.  **[収集間隔 (ミリ秒)]** ボックスに、間隔を入力します。  
  
5.  **[カウンター カテゴリ]** ドロップダウン リストで、カテゴリを選択します。  
  
6.  **[インスタンス]** ドロップダウン リストで、インスタンスを選択します。  
  
7.  アプリケーションをプロファイルするときに使用するカウンターを選択します。  
  
8.  **[適用]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [パフォーマンス セッションのプロパティ](../profiling/performance-session-properties.md)   
 [CPU カウンターと Windows カウンター](../profiling/cpu-and-windows-counters.md)