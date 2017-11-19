---
title: "IActiveScript::GetScriptThreadState |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
スクリプトのスレッドの現在の状態を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stidThread`  
 [in]対象の状態が必要な場合、スレッドの識別子、または次の特殊なスレッド id のいずれか:  
  
|値|説明|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|基本スレッドです。つまりをスクリプト エンジンのスレッドがインスタンス化されます。|  
|SCRIPTTHREADID_CURRENT|現在実行中のスレッド。|  
  
 `pstsState`  
 [out]指定されたスレッドの状態を受け取る変数のアドレスです。 によって定義された名前付き定数値のいずれかによって状態が示される、 [SCRIPTTHREADSTATE 列挙](../../winscript/reference/scriptthreadstate-enumeration.md)列挙します。 このパラメーターが、現在のスレッドを特定できない場合は、状態はいつでも変更できます。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) します。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、ホスト オブジェクトまたはベース以外吹き出しの結果として得られることがなくベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)