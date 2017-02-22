---
title: "Attach | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Attach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Attach** オプションは、プロセス ID \(PID\) で指定された実行中のプロセスのサンプル プロファイルを開始します。  
  
 **Attach** オプションを使用するには、Start オプションで **Sample** メソッドを指定する必要があります。  
  
> [!NOTE]
>  **Start** オプションと共に **Crosssession** オプションが指定されている場合は、**VSPerfCmd \/Attach** または **VSPerfCmd \/Detach** への呼び出しでも **Crosssession** を指定する必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### パラメーター  
 `ProcessID`  
 実行中のプロセスのプロセス ID \(PID\)。  実行中のプロセスの PID は、Windows タスク マネージャーの \[プロセス\] タブに表示されます。  
  
## 有効なオプション  
 **Attach** オプションと組み合わせて 1 行のコマンド ラインで指定できる **VSPerfCmd** オプションを次に示します。  
  
 **Crosssession**  
 ログオン セッション以外のセッションにおけるアプリケーションのプロファイリングを有効にします。  **Start** オプションと共に **Crosssession** オプションが指定された場合は必須です。  
  
 **Start:** `Method`  
 コマンド ライン プロファイラー セッションを初期化し、指定されたプロファイル方法を設定します。  
  
 **TargetCLR**  
 プロファイル セッションに複数バージョンの .NET Framework 共通言語ランタイム \(CLR: Common Language Runtime\) が読み込まれている場合に、プロファイルを行う CLR のバージョンを指定します。  既定では、最初に読み込まれたバージョンがプロファイルされます。  
  
 **GlobalOn GlobalOff**  
 プロファイリングを再開 \(**GlobalOn**\) または一時停止 \(**GlobalOff**\) しますが、プロファイル セッションは終了しません。  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 指定されたプロセスのプロファイリングを再開 \(**ProcessOn**\) または一時停止 \(**ProcessOff**\) します。  
  
## 間隔オプション  
 Attach のコマンド ラインでは、次のサンプリング間隔オプションのうちのいずれか 1 つを指定できます。  既定のサンプリング間隔は、プロセッサのクロック サイクル数 10,000,000 です。  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**Events\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]  
 サンプリング間隔の数値と種類を指定します。  
  
-   **Timer**: プロセッサのクロック サイクル数が `Cycles` で指定された回数に到達するたびにサンプリングを行います。  `Cycles` が指定されていない場合は、10,000,000 サイクルに設定されます。  
  
-   **PF**: ページ フォールト数が `Events` で指定された回数に到達するたびにサンプリングを行います。  `Events` が指定されていない場合は、ページ フォールト数 10 回に設定されます。  
  
-   **Sys**: オペレーティング システムへの呼び出しが `Events` で指定された回数に到達するたびにサンプリングを行います。  `Events` が指定されていない場合は、システム コール 10 回に設定されます。  
  
-   **Counter**: `Name` で指定された CPU のパフォーマンス カウンターが、`Reload` で指定された数値に到達するたびにサンプリングを行います。  オプションとして、`FriendlyName` でプロファイラー レポート内の列ヘッダーとして使用する文字列を指定できます。  
  
## 使用例  
 次の例では、アプリケーションの実行中のインスタンス \(プロセス ID 12345\) にプロファイラーをアタッチする方法を示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)