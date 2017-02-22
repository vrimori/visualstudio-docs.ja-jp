---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

実行可能ファイルが起動されます。  
  
## 構文  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```c#  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### パラメーター  
 `pszExe`  
 \[入力\] 起動する実行可能ファイルの名前。  これは `pszDir` のパラメーターで指定される作業ディレクトリに対する完全パスまたはです。  
  
 `pszArgs`  
 \[入力\] 実行可能ファイルに渡される引数。  引数がない場合は null 値を指定できます。  
  
 `pszDir`  
 \[入力\] 実行可能ファイルによって使用される作業ディレクトリの名前。  作業ディレクトリが必要ない場合は null 値を指定できます。  
  
 `bstrEnv`  
 \[入力\] 追加 null 終端文字を指定する NULL で終わる文字列の環境ブロック。  
  
 `hStdInput`  
 \[入力\] 値を代替の入力ストリームへのハンドル。  リダイレクトする必要がない場合は 0 を指定できます。  
  
 `hStdOutput`  
 \[入力\] 値を代替の出力ストリームへのハンドル。  リダイレクトする必要がない場合は 0 を指定できます。  
  
 `hStdError`  
 \[入力\] 値を代替のエラー出力ストリームへのハンドル。  リダイレクトする必要がない場合は 0 を指定できます。  
  
 `ppPortProcess`  
 \[入力\] 起動したプロセスを表す [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはプロセスを開始し中断したコードは実行されません。  [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) の場合プロセスを再開されます。  
  
 プログラムがデバッグ エンジンから起動できます。  詳細については、「[プログラムの起動](../../../extensibility/debugger/launching-a-program.md)」を参照してください。  
  
## 参照  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [プログラムの起動](../../../extensibility/debugger/launching-a-program.md)