---
title: IActiveScript::GetScriptThreadState |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b191f1b70aa522cba0a04e0781ada69a8fe5ca5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097527"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
スクリプトのスレッドの現在の状態を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stidThread`  
 [in]対象の状態が必要に応じて、スレッドの識別子、または次の特殊なスレッド識別子のいずれか:  
  
|[値]|説明|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|基本スレッドです。つまり、これで、スクリプト エンジンのスレッドがインスタンス化されました。|  
|SCRIPTTHREADID_CURRENT|現在実行中のスレッド。|  
  
 `pstsState`  
 [out]指定されたスレッドの状態を受け取る変数のアドレス。 によって定義された名前付き定数の値のいずれかによって状態が示される、 [SCRIPTTHREADSTATE 列挙型](../../winscript/reference/scriptthreadstate-enumeration.md)列挙体。 このパラメーターが、現在のスレッドを特定できない場合は、状態がいつでもでも変更可能性があります。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) します。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ホスト オブジェクトまたはベース以外の吹き出しでベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)