---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはデバッグ エンジン \(DE\) によってプロセスを起動します。  
  
## 構文  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```c#  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### パラメーター  
 `pszMachine`  
 \[入力\] プロセスを開始するコンピューターの名前。  ローカル コンピューターを指定するにはnull 値を使用します。  
  
 `pPort`  
 \[入力\] プログラムを実行するポートを表す [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) のインターフェイス。  
  
 `pszExe`  
 \[入力\] 起動する実行可能ファイルの名前。  
  
 `pszArgs`  
 \[入力\] 実行可能ファイルに渡される引数。  引数がない場合は null 値を指定できます。  
  
 `pszDir`  
 \[入力\] 実行可能ファイルによって使用される作業ディレクトリの名前。  作業ディレクトリが必要ない場合は null 値を指定できます。  
  
 `bstrEnv`  
 \[入力\] 追加 null 終端文字を指定する NULL で終わる文字列の環境ブロック。  
  
 `pszOptions`  
 \[入力\] 実行可能ファイルのオプション。  
  
 `dwLaunchFlags`  
 \[入力\] セッションに対して [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) を指定します。  
  
 `hStdInput`  
 \[入力\] 値を代替の入力ストリームへのハンドル。  リダイレクトする必要がない場合は 0 を指定できます。  
  
 `hStdOutput`  
 \[入力\] 値を代替の出力ストリームへのハンドル。  リダイレクトする必要がない場合は 0 を指定できます。  
  
 `hStdError`  
 \[入力\] 値を代替のエラー出力ストリームへのハンドル。  リダイレクトする必要がない場合は 0 を指定できます。  
  
 `pCallback`  
 \[入力\] デバッガー イベントを受け取る [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のオブジェクト。  
  
 `ppDebugProcess`  
 \[入力\] 起動したプロセスを表す [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 結果のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 通常[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] は [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) のメソッドを使用してプログラムを起動し次に中断中のプログラムにデバッガーをアタッチします。  ただしデバッグ エンジン \(デバッグ エンジンがある場合はデバッグとインタープリター プログラムの一部は解釈される言語\) プログラムを起動する必要がある場合は状況がありますが[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]`IDebugEngineLaunch2::LaunchSuspended` のメソッドを使用します。  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) の場合プロセスが中断状態に開始後にプロセスを起動するために呼び出されます。  
  
## 参照  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)