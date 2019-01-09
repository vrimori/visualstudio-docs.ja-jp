---
title: IActiveScript::GetScriptThreadID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b1c68d60b827e7540711cdf6ba34260fb8642ed
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094875"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
特定の Win32 スレッドに関連付けられているスレッドのスクリプト エンジン定義の識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwWin32ThreadID` ,  
 [in]現在のプロセスで実行中の Win32 スレッドのスレッドの識別子。 使用して、 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)現在実行中のスレッドのスレッド識別子を取得します。  
  
 `pstidThread` ,  
 [out]特定の Win32 スレッドに関連付けられているスクリプトのスレッド識別子を受け取る変数のアドレス。 この識別子の解釈は、スクリプト エンジンへのままですが、Windows スレッド id のコピーだけができます。 Win32 スレッドが終了した場合はこの識別子が割り当てられていないを後で別のスレッドに割り当てることができますに注意してください。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) し、そのために失敗しました。|  
  
## <a name="remarks"></a>Remarks  
 取得した識別子をなどのスクリプト スレッド実行の制御メソッドを後続の呼び出しで使用できます、 [iactivescript::interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)メソッド。  
  
 このメソッドは、ホスト オブジェクトまたはベース以外の吹き出しでベース以外のスレッドから呼び出すことができます、 [iactivescript::interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)