---
title: IDebugEngineLaunch2::LaunchSuspended |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a05e8f034ec30f0f387675759cb7601f7b3fc3e7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
このメソッドは、デバッグ エンジン (DE) を使用して、プロセスを起動します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>パラメーター  
 `pszMachine`  
 [in]プロセスを起動するコンピューターの名前。 ローカル コンピューターを指定するのにには、null 値を使用します。  
  
 `pPort`  
 [in][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)プログラムを実行するポートを表すインターフェイス。  
  
 `pszExe`  
 [in]起動する実行可能ファイルの名前。  
  
 `pszArgs`  
 [in]実行可能ファイルに渡す引数。 引数がない場合、null 値を指定できます。  
  
 `pszDir`  
 [in]実行可能ファイルによって使用される作業ディレクトリの名前。 作業ディレクトリが必要ない場合、null 値があります。  
  
 `bstrEnv`  
 [in]その他の NULL 終端記号を NULL で終わる文字列の環境ブロックします。  
  
 `pszOptions`  
 [in]実行可能ファイルのオプションです。  
  
 `dwLaunchFlags`  
 [in]指定します、 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)セッションです。  
  
 `hStdInput`  
 [in]代替の入力ストリームを処理します。 リダイレクトが必要ない場合 0 にすることがあります。  
  
 `hStdOutput`  
 [in]代替の出力ストリームへのハンドルします。 リダイレクトが必要ない場合 0 にすることがあります。  
  
 `hStdError`  
 [in]代替のエラー出力ストリームへのハンドルします。 リダイレクトが必要ない場合 0 にすることがあります。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッガー イベントを受け取るオブジェクトです。  
  
 `ppDebugProcess`  
 [out]その結果を返します[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)を実行中のプロセスを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 通常、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]を使用してプログラムを起動、 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)メソッドを中断されているプログラムにデバッガーをアタッチします。 ただし、デバッグ エンジンがいる場合 (たとえば、デバッグ エンジンは、インタープリターの一部と、デバッグ中のプログラムは、解釈された言語の場合)、プログラムを起動する必要がありますの状況がある[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]を使用して、`IDebugEngineLaunch2::LaunchSuspended`メソッド.  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)プロセスが中断状態に正常に起動した後、プロセスを開始するメソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)