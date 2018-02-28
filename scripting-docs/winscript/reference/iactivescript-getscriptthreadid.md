---
title: "IActiveScript::GetScriptThreadID |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
特定の Win32 スレッドに関連付けられているスレッドのスクリプト エンジン定義の識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwWin32ThreadID` ,  
 [in]現在のプロセスで実行中の Win32 スレッドのスレッドの識別子。 使用して、 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)実行中のスレッドのスレッド識別子を取得します。  
  
 `pstidThread` ,  
 [out]特定の Win32 スレッドに関連付けられているスクリプトのスレッド識別子を受け取る変数のアドレスです。 この識別子の解釈は、スクリプト エンジンに左しますが、Windows のスレッドの識別子のコピーだけを指定できます。 Win32 スレッドが終了した場合はこの識別子が割り当てられていないと、後で別のスレッドに割り当てることができますに注意してください。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) し、そのために失敗しました。|  
  
## <a name="remarks"></a>コメント  
 取得した識別子をなど、スクリプトのスレッドの実行の制御方法を後続の呼び出しで使用できます、 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)メソッドです。  
  
 このメソッドは、ホスト オブジェクトまたはベース以外吹き出しの結果として得られることがなくベース以外のスレッドから呼び出すことができます、 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)