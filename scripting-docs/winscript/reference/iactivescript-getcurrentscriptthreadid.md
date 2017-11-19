---
title: "IActiveScript::GetCurrentScriptThreadID |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
現在実行中のスレッドのスクリプト エンジン定義の識別子を取得します。 識別子をなどスクリプト スレッドの実行制御のメソッドへの後続の呼び出しで使用できる、 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstidThread`  
 [out]現在のスレッドに関連付けられているスクリプトのスレッド識別子を受け取る変数のアドレスです。 この識別子の解釈は、スクリプト エンジンに左しますが、Windows のスレッドの識別子のコピーだけを指定できます。 Win32 スレッド終了した場合、この識別子は割り当てられていないようになり、別のスレッドに、後で割り当てられていることができます。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_POINTER`に無効なポインターが指定されている場合。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、ホスト オブジェクトまたはベース以外吹き出しの結果として得られることがなくベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)