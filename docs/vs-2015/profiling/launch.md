---
title: Launch | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e94bb407255f490c0c5423ef355581790c622395
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546274"
---
# <a name="launch"></a>Launch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[起動](https://docs.microsoft.com/visualstudio/profiling/launch)します。  
  
**Launch** オプションは、サンプリング メソッドを使用するプロファイラーを起動し、指定されたアプリケーションも起動します。  
  
 **Launch** オプションを使用するには、**Start** オプションで **Sample** メソッドを指定する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `AppName`  
 起動するアプリケーションの名前。 現在のディレクトリからの完全パスおよび部分パスがサポートされます。  
  
## <a name="valid-options"></a>有効なオプション  
 **Launch** オプションと組み合わせて単一コマンド ラインで指定できる VSPerfCmd オプションを以下に示します。  
  
 **Start:** `Method`  
 コマンド ライン プロファイラー セッションを初期化し、指定されたプロファイル方法を設定します。  
  
 **GlobalOn** および **GlobalOff**  
 プロファイリングを再開 (**GlobalOn**) または一時停止 (**GlobalOff**) しますが、プロファイル セッションは終了しません。  
  
 **ProcessOn:** `PID` および **ProcessOff**:`PID`  
 指定されたプロセスのプロファイリングを再開 (**ProcessOn**) または一時停止 (**ProcessOff**) します。  
  
 **TargetCLR**  
 プロファイル セッションに複数バージョンの .NET Framework 共通言語ランタイム (CLR) が読み込まれている場合に、プロファイルを行う CLR のバージョンを指定します。 既定では、最初に読み込まれたバージョンがプロファイルされます。  
  
## <a name="exclusive-options"></a>排他的なオプション  
 次のオプションは、**Launch** オプションと共に指定する場合にのみ使用できます。  
  
 **コンソール**  
 指定されたコマンド ライン アプリケーションを新しいウィンドウで起動します。  
  
 **Args:** `ArgList`  
 アプリケーションに渡す引数リストを指定します。  
  
 **LineOff**  
 行レベルのプロファイル データの収集を無効にします。  
  
## <a name="sampling-options"></a>サンプリングのオプション  
 **Launch** コマンド ラインでは、次のサンプリング間隔オプションのいずれかを指定できます。 既定のサンプリング間隔は、10,000,000 プロセッサ クロック サイクルです。  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**allocation**&#124;**lifetime**]  
 サンプリング間隔の数値と種類を指定します。  
  
-   **Timer** - `Cycles` のプロセッサ クロック サイクル (停止なし) ごとにサンプリングを行います。 `Cycles` が指定されていない場合、10,000,000 サイクルが使用されます。  
  
-   **PF** - `Events` のページ フォールトごとにサンプリングを行います。 `Events` が指定されていない場合は、10 ページ フォールトになります。  
  
-   **Sys** - オペレーティング システムへの `Events` の呼び出しごとにサンプリングを行います。 `Events` が指定されていない場合は、10 システム呼び出しが使用されます。  
  
-   **Counter** - `Name` で指定された CPU パフォーマンス カウンターの `Reload` の数値ごとにサンプリングを行います。 必要に応じて、`FriendlyName` でプロファイラー レポート内の列ヘッダーとして使用する文字列を指定できます。  
  
-   **GC** - .NET メモリ データを収集します。 既定 (**allocation**) では、データはメモリの割り当てイベントごとに収集されます。 **lifetime** パラメーターが指定されている場合、ガベージ コレクション イベントごとのデータも収集されます。  
  
## <a name="example"></a>例  
 **Launch** を使用してアプリケーションを起動する例を以下に示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



