---
title: "IActiveScript::GetScriptState |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285a09308c7477dbeed68f9f93417b503ca4fe49
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
スクリプト エンジンの現在の状態を取得します。 このメソッドは、ホスト オブジェクトまたはベース以外吹き出しの結果として得られることがなくベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pss`  
 [out]定義されている値を受け取る変数のアドレス、 [SCRIPTSTATE 列挙](../../winscript/reference/scriptstate-enumeration.md)列挙します。 値は、呼び出し元のスレッドに関連付けられているスクリプト エンジンの現在の状態を示します。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_POINTER`に無効なポインターが指定されている場合。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)