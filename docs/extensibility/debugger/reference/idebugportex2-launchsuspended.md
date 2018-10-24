---
title: IDebugPortEx2::LaunchSuspended |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a16241e406ea89b33c417bd873949979c3f6e82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882315"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
実行可能ファイルを起動します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>パラメーター  
 `pszExe`  
 [in]起動する実行可能ファイルの名前。 完全なパスまたは相対で指定された作業ディレクトリを指定できます、`pszDir`パラメーター。  
  
 `pszArgs`  
 [in]実行可能ファイルに渡す引数。 引数がない場合、null 値を指定できます。  
  
 `pszDir`  
 [in]実行可能ファイルで使用される作業ディレクトリの名前。 作業ディレクトリが必要ない場合、null 値があります。  
  
 `bstrEnv`  
 [in]追加の NULL 終端記号の後に、null で終わる文字列の環境ブロックします。  
  
 `hStdInput`  
 [in]代替の入力ストリームへのハンドルします。 リダイレクトが必要でない場合は、0 を指定できます。  
  
 `hStdOutput`  
 [in]代替の出力ストリームへのハンドルします。 リダイレクトが必要でない場合は、0 を指定できます。  
  
 `hStdError`  
 [in]代替エラー出力ストリームへのハンドルします。 リダイレクトが必要でない場合は、0 を指定できます。  
  
 `ppPortProcess`  
 [out]返します、 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)実行中のプロセスを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、その it が中断されているため、プロセスと、コードが実行されていないを起動する必要があります。 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)メソッドが呼び出され、プロセスを再開します。  
  
 プログラムは、デバッグ エンジンからも起動できます。 詳細については、次を参照してください。[プログラムの起動](../../../extensibility/debugger/launching-a-program.md)します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [プログラムの起動](../../../extensibility/debugger/launching-a-program.md)