---
title: IDebugEngineLaunch2::LaunchSuspended |Microsoft Docs
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
ms.openlocfilehash: ffe5bdd0619ae5954a34fde50518adb3767d1825
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926502"
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
 [in]プロセスを起動するマシンの名前。 ローカル コンピューターを指定するのにには、null 値を使用します。  
  
 `pPort`  
 [in][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)プログラムで実行されるポートを表すインターフェイス。  
  
 `pszExe`  
 [in]起動する実行可能ファイルの名前。  
  
 `pszArgs`  
 [in]実行可能ファイルに渡す引数。 引数がない場合、null 値を指定できます。  
  
 `pszDir`  
 [in]実行可能ファイルで使用される作業ディレクトリの名前。 作業ディレクトリが必要ない場合、null 値があります。  
  
 `bstrEnv`  
 [in]追加の NULL 終端記号の後に、NULL で終わる文字列の環境ブロックします。  
  
 `pszOptions`  
 [in]実行可能ファイルのオプションです。  
  
 `dwLaunchFlags`  
 [in]指定します、 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)セッション。  
  
 `hStdInput`  
 [in]代替の入力ストリームへのハンドルします。 リダイレクトが必要でない場合は、0 を指定できます。  
  
 `hStdOutput`  
 [in]代替の出力ストリームへのハンドルします。 リダイレクトが必要でない場合は、0 を指定できます。  
  
 `hStdError`  
 [in]代替エラー出力ストリームへのハンドルします。 リダイレクトが必要でない場合は、0 を指定できます。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッガー イベントを受け取るオブジェクト。  
  
 `ppDebugProcess`  
 [out]結果を返します[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)実行中のプロセスを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 通常、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]を使用してプログラムを起動、 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)メソッドと中断されたプログラムにデバッガーをアタッチします。 ただし、この場合 (たとえば、デバッグ エンジンは、インタープリターの一部と、デバッグ中のプログラムはインタープリター言語である場合)、プログラムを起動する必要があります、デバッグ エンジンの状況がある[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]を使用して、`IDebugEngineLaunch2::LaunchSuspended`メソッド.  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)プロセスが中断状態に正常に起動した後、プロセスを開始するメソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)