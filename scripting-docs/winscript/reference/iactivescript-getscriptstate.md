---
title: IActiveScript::GetScriptState |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a64067679e1c56831002494c579ffdeba84a1abe
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346632"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
スクリプト エンジンの現在の状態を取得します。 このメソッドは、ホスト オブジェクトまたはベース以外の吹き出しでベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイス。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pss`  
 [out]定義されている値を受け取る変数のアドレス、 [SCRIPTSTATE 列挙型](../../winscript/reference/scriptstate-enumeration.md)列挙体。 値は、呼び出し元のスレッドに関連付けられているスクリプト エンジンの現在の状態を示します。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_POINTER`場合は、無効なポインターが指定されました。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)