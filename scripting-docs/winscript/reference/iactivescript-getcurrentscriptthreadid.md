---
title: IActiveScript::GetCurrentScriptThreadID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bac3b5755328e643c26c8f3746af6648d8ac06aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345800"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
現在実行中のスレッドのスクリプト エンジン定義の識別子を取得します。 識別子をなどのスクリプト スレッド実行の制御メソッドへの後続の呼び出しで使用できます、 [iactivescript::interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstidThread`  
 [out]現在のスレッドに関連付けられているスクリプトのスレッド識別子を受け取る変数のアドレス。 この識別子の解釈は、スクリプト エンジンへのままですが、Windows スレッド id のコピーだけができます。 Win32 スレッドが終了した場合はこの識別子は割り当てられていないようになり、別のスレッドに割り当てることができます、その後。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_POINTER`場合は、無効なポインターが指定されました。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ホスト オブジェクトまたはベース以外の吹き出しでベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)