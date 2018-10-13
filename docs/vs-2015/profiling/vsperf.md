---
title: VSPerf | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b36e33bb589e2866a14acd9dc253af78d7d9c7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176049"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VsPerf** コマンド ライン ツールを使用して、次を行います。  
  
1.  Visual Studio がデバイスにインストールされていない場合、Windows ストア アプリをコマンド ラインからプロファイルします。  
  
2.  サンプリング プロファイル方法を使用して、Windows 8 デスクトップ アプリケーションと Windows Server 2012 アプリケーションをプロファイルします。  
  
 プロファイル オプションの詳細については、「[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 このトピックでは、`vsperf.exe` コマンド ライン ツールで使用できるオプションについて説明します。 このトピックは、次のセクションで構成されています。  
  
 [Windows ストア アプリのみ](#BKMK_windows_store_apps_only)  
  
 [Windows 8 デスクトップ アプリケーション、および Windows Server 2012 のアプリケーションのみ](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [すべてのアプリケーション](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Windows ストア アプリのみ  
 これらのオプションは、Windows ストア アプリにのみ適用されます。  
  
|||  
|-|-|  
|**/app:{AppName}**|プロファイラーを起動し、スタート メニューから起動される指定したアプリを待機します。<br /><br /> `vsperf /listapps` を実行して、インストール済みアプリの Name と PackageFullName を表示します。|  
|**/package:{PackageFullName}**|プロファイラーを起動し、スタート メニューから起動される指定したアプリを待機します。<br /><br /> `vsperf /listapps` を実行して、インストール済みアプリの Name と PackageFullName を表示します。|  
|**/js**|JavaScript アプリのプロファイルを行うために必要です。<br /><br /> JavaScript アプリからパフォーマンス データを収集します。<br /><br /> /package または /attach でのみ使用します。|  
|**/noclr**|任意。 CLR データは収集しません。<br /><br /> /package または /attach でのみ使用します。<br /><br /> 最適化で、マネージド シンボルは解決されません。|  
|**/listapps**|インストール済みアプリの Name と PackageFullName を一覧表示します。|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Windows 8 デスクトップ アプリケーション、および Windows Server 2012 のアプリケーションのみ  
 これらのオプションは、Windows ストア アプリでは機能しません。  
  
|||  
|-|-|  
|**/launch:{Executable}**|指定した実行可能ファイルのプロファイルを起動して開始します。|  
|**/args:{ExecutableArguments}**|**/launch** ターゲットに渡すようにコマンド ライン引数を指定します。|  
|**/console**|新しいコマンド ウィンドウで **/launch** ターゲットを実行します。|  
  
##  <a name="BKMK_All_applications"></a> すべてのアプリケーション  
 これらのオプションは、すべての Windows 8 アプリケーションまたは Windows Server 2012 アプリケーションに適用されます。  
  
|||  
|-|-|  
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|指定したプロセスからデータを収集します。<br /><br /> タスク マネージャーを使用して、実行中のアプリのプロセス ID (PID) とプロセス名を表示します。|  
|**/file:{ReportName}**|任意。 出力ファイルを指定します (既存のファイルを上書き)。<br /><br /> /package または /attach でのみ使用します。|  
|**/pause**|データ収集を一時停止します。|  
|**/resume**|データ収集を再開します。|  
|**/stop**|データ収集を停止し、ターゲット プロセスを終了します。|  
|**/detach**|データ収集を停止しますが、ターゲット プロセスの実行は続行します。|  
|**/status**|プロファイラーの状態を表示します。|  
  
## <a name="see-also"></a>関連項目  
 [Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [コマンド ラインからのプロファイル](../profiling/using-the-profiling-tools-from-the-command-line.md)



