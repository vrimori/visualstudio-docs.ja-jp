---
title: "コマンド ラインからのプロファイリング ツールの使用 | Microsoft Docs"
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
  - "コマンド ライン、パフォーマンス ツール"
  - "コマンド ライン ツール、パフォーマンス ツール"
  - "プロファイリング ツール、コマンド ライン"
  - "ツール、コマンド ライン"
  - "コマンド ライン、ツール"
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# コマンド ラインからのプロファイリング ツールの使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールを使用して、コマンド プロンプトでアプリケーションをプロファイリングしたり、バッチ ファイルやスクリプトでプロファイリングを自動化したりできます。  コマンド プロンプトでレポート ファイルを生成することもできます。  スタンドアロンの簡易プロファイラーを使用すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がインストールされていないコンピューター上のデータを収集できます。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。  Windows ストア アプリにも新しい収集手法が必要です。  「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**シンボルの場所の設定:** 関数とパラメーターの名前を表示するには、プロファイラーがプロファイリング対象のバイナリのシンボル ファイル \(.pdb\) にアクセスできる必要があります。  これらのファイルには、分析で表示する Microsoft オペレーティング システムおよびアプリケーション用のシンボル ファイルが含まれている必要があります。  Microsoft パブリック シンボル サーバーを使用して、Microsoft バイナリ用の正しい .pdb ファイルがあるかどうかを確認できます。|-   [方法: コマンド ラインからシンボル ファイルの場所を指定する](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**アプリケーションのプロファイリング:** ターゲット アプリケーションのプロファイリングに使用するコマンド ライン ツールとオプションは、アプリケーションの種類、プロファイリングの方法、およびターゲット アプリケーションがマネージ アプリケーションであるかネイティブ アプリケーションであるかによって異なります。|-   [コマンド ラインからのプロファイル方法の使用](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)|  
|**.xml レポートおよび .csv レポートの作成:** コマンド プロンプトでプロファイリングを実行すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のインターフェイスで表示できるデータ ファイルが作成されます。  コマンド ライン ツール VSPerfReport を使用して、データの .xml ファイルまたはコンマ区切り値 \(.csv\) ファイルを生成することもできます。|-   [コマンド ラインからのプロファイラー レポートの作成](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Visual Studio がインストールされていないコンピューター上のコードのプロファイリング:** プロファイリング ツールのスタンドアロンのプロファイラーを使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がインストールされていないコンピューター上のアプリケーションのデータを収集できます。|-   [方法 : スタンドアロンのプロファイラーをインストールする](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## 参照  
 [コマンド ライン プロファイリング ツール リファレンス](../profiling/command-line-profiling-tools-reference.md)  
  
## 参照  
 [プロファイリング ツールの使用](../profiling/performance-explorer.md)