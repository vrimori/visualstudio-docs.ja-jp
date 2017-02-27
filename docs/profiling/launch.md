---
title: "Launch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Launch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Launch** オプションは、サンプリング メソッドを使用するプロファイラーを起動し、指定されたアプリケーションも起動します。  
  
 **Launch** オプションを使用するには、**Start** オプションで **Sample** メソッドを指定する必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### パラメーター  
 `AppName`  
 起動するアプリケーションの名前。  現在のディレクトリからの完全パスおよび部分パスがサポートされます。  
  
## 有効なオプション  
 **Launch** オプションと組み合わせて 1 行のコマンド ラインで指定できる VSPerfCmd オプションを次に示します。  
  
 **Start:** `Method`  
 コマンド ライン プロファイラー セッションを初期化し、指定されたプロファイル方法を設定します。  
  
 **GlobalOn** および **GlobalOff**  
 プロファイリングを再開 \(**GlobalOn**\) または一時停止 \(**GlobalOff**\) しますが、プロファイル セッションは終了しません。  
  
 **ProcessOn:** `PID` および **ProcessOff**:`PID`  
 指定されたプロセスのプロファイリングを再開 \(**ProcessOn**\) または一時停止 \(**ProcessOff**\) します。  
  
 **TargetCLR**  
 プロファイル セッションに複数バージョンの .NET Framework 共通言語ランタイム \(CLR: Common Language Runtime\) が読み込まれている場合に、プロファイルを行う CLR のバージョンを指定します。  既定では、最初に読み込まれたバージョンがプロファイルされます。  
  
## 排他的オプション  
 次のオプションは、**Launch** オプションを使用する場合にのみ使用できます。  
  
 **Console**  
 指定されたコマンド ライン アプリケーションを新しいウィンドウで起動します。  
  
 **Args:** `ArgList`  
 起動したアプリケーションに渡す引数リストを指定します。  
  
 **LineOff**  
 行レベルのプロファイル データの収集を無効にします。  
  
## サンプリングのオプション  
 **Launch** のコマンド ラインでは、次のサンプリング間隔オプションのうちのいずれか 1 つを指定できます。  既定のサンプリング間隔は、プロセッサのクロック サイクル数 10,000,000 です。  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 サンプリング間隔の数値と種類を指定します。  
  
-   **Timer**: プロセッサのクロック サイクル数 \(停止なし\) が `Cycles` で指定された回数に到達するたびにサンプリングを行います。  `Cycles` が指定されていない場合は、10,000,000 サイクルに設定されます。  
  
-   **PF**: ページ フォールト数が `Events` で指定された回数に到達するたびにサンプリングを行います。  `Events` が指定されていない場合は、ページ フォールト数 10 回に設定されます。  
  
-   **Sys**: オペレーティング システムへの呼び出しが `Events` で指定された回数に到達するたびにサンプリングを行います。  `Events` が指定されていない場合は、システム コール 10 回に設定されます。  
  
-   **Counter**: `Name` で指定された CPU のパフォーマンス カウンターが、`Reload` で指定された数値に到達するたびにサンプリングを行います。  オプションとして、`FriendlyName` でプロファイラー レポート内の列ヘッダーとして使用する文字列を指定できます。  
  
-   **GC**: .NET メモリ データを収集します。  既定 \(**allocation**\) では、データはメモリの割り当てイベントごとに収集されます。  **lifetime** パラメーターが指定された場合、ガベージ コレクション イベントごとのデータも収集されます。  
  
## 使用例  
 **Launch** を使用してアプリケーションを起動する例を次に示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)