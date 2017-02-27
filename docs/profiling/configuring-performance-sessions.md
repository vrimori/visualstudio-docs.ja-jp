---
title: "プロファイリング ツールのパフォーマンス セッションの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "一般的なタスク、パフォーマンス"
  - "一般的なタスク、プロファイリング ツール"
  - "プロファイリング ツール、一般的なタスク"
  - "パフォーマンス、データの収集"
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 36
---
# プロファイリング ツールのパフォーマンス セッションの構成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールを使用すると、さまざまな種類のアプリケーションのさまざまなパフォーマンス データを収集することができます。  ここでは、パフォーマンス ウィザードおよびパフォーマンス セッションとターゲット バイナリのプロパティを使用して、対象とするデータを収集するようにプロファイリング ツールを構成する方法を示します。  プロファイリング実行で収集するデータの量を制御するために、プロファイリング ツールの構成プロパティも使用できます。  詳細については、「[データ収集の制御](../profiling/controlling-data-collection.md)」を参照してください。  
  
> [!NOTE]
>  多くの場合、パフォーマンス ウィザードの既定のプロパティを使用することは、プロファイリング データの収集に効果的な方法です。  詳細については、「[パフォーマンス プロファイリングのビギナーズ ガイド](../profiling/beginners-guide-to-performance-profiling.md)」および「[作業の開始](../profiling/getting-started-with-performance-tools.md)」を参照してください。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**基本のプロファイリング オプションを設定する:** Microsoft シンボル サーバーを使用するように [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] を構成する必要があります。  そうすることにより、Windows および他の Microsoft アプリケーションの現在のバージョンで、関数名やパラメーター名などのシンボルへのアクセスを確保できます。  プロファイリング セッションが開始する前に、プロファイリング ツールへのシステムのアクセス許可やプロファイリング データ ファイルの名前など、他の一般的なオプションを指定することもできます。|-   [方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [方法: シンボル情報をシリアル化する](../profiling/how-to-serialize-symbol-information.md)<br />-   [方法: 現在のプロファイリング セッションを設定する](../Topic/How%20to:%20Set%20the%20Current%20Session.md)<br />-   [方法 : プロファイリングのアクセス許可を設定する](../profiling/how-to-set-permissions.md)<br />-   [方法: プロファイル データ ファイル名のオプションを設定する](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**収集するデータを指定する:** プロファイリング セッションの構成に使用する手順は、プロファイル対象のアプリケーションおよび収集するパフォーマンス データの種類に応じて変わります。|-   [方法 : 収集方法を選択する](../profiling/how-to-choose-collection-methods.md)<br />-   [サンプリングを使用したパフォーマンス統計情報の収集](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [.NET メモリの割り当ておよび有効期間データの収集](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [方法: Web ページ内の JavaScript \(ECMA\) コードをプロファイリングする](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [スレッドおよびプロセスの同時実行データの収集](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [追加のパフォーマンス データの収集](../profiling/collecting-additional-performance-data.md)|  
|**高度な構成オプションを設定する:** 共通言語ランタイム \(CLR\) の複数のバージョンを読み込む .NET Framework アプリケーションに対してプロファイルを行う場合は、プロファイルを行う対象のバージョンを指定できます。  パフォーマンス セッションに複数の .exe ファイルがある場合は、バイナリの開始順序を設定できます。|-   [方法: side\-by\-side 実行でプロファイリングするように .NET Framework ランタイムを指定する](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)<br />-   [方法 : 開始するバイナリを指定する](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## 関連項目  
 [データ収集の制御](../profiling/controlling-data-collection.md)  
  
## 参照  
 [プロファイリング ツールの使用](../profiling/performance-explorer.md)