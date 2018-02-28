---
title: "IDebugPortEx2::LaunchSuspended |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f78561bed8170d71ed608183543a487b765f792b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
 [in]起動する実行可能ファイルの名前。 これで指定された作業ディレクトリへの相対パスまたは完全なパスを指定できます、`pszDir`パラメーター。  
  
 `pszArgs`  
 [in]実行可能ファイルに渡す引数。 引数がない場合、null 値を指定できます。  
  
 `pszDir`  
 [in]実行可能ファイルによって使用される作業ディレクトリの名前。 作業ディレクトリが必要ない場合、null 値があります。  
  
 `bstrEnv`  
 [in]その他の NULL 終端記号を null で終わる文字列の環境ブロックします。  
  
 `hStdInput`  
 [in]代替の入力ストリームを処理します。 リダイレクトが必要ない場合 0 にすることがあります。  
  
 `hStdOutput`  
 [in]代替の出力ストリームへのハンドルします。 リダイレクトが必要ない場合 0 にすることがあります。  
  
 `hStdError`  
 [in]代替のエラー出力ストリームへのハンドルします。 リダイレクトが必要ない場合 0 にすることがあります。  
  
 `ppPortProcess`  
 [out]返します、 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)を実行中のプロセスを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドには、it が中断されているため、プロセスと任意のコードが実行されていないを起動する必要があります。 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)プロセスを再開するメソッドが呼び出されます。  
  
 デバッグ エンジンからプログラムを起動することもできます。 詳細については、「[プログラムの起動](../../../extensibility/debugger/launching-a-program.md)です。  
  
## <a name="see-also"></a>参照  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [プログラムの起動](../../../extensibility/debugger/launching-a-program.md)