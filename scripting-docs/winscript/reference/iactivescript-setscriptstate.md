---
title: IActiveScript::SetScriptState |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645672"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
スクリプト エンジンを実行すると、指定された状態になります。 このメソッドは、ホスト オブジェクトまたはベース以外吹き出しの結果として得られることがなくベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ss`  
 [in]指定された状態をスクリプト エンジンを設定します。 定義されている値のいずれかになります、 [SCRIPTSTATE 列挙](../../winscript/reference/scriptstate-enumeration.md)列挙します。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|スクリプト エンジンが初期化された状態に遷移をサポートしていません。 ホストする必要がありますこのスクリプト エンジンを破棄し作成、初期化、および同じ効果を実現するために新しいスクリプト エンジンを読み込みます。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) し、そのために失敗しました。|  
|`OLESCRIPT_S_PENDING`|メソッドが正常にキューに登録が状態がまだ変更されていません。 ときに状態の変化、サイトがコールバックされるを通じて、 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)メソッドです。|  
|`S_FALSE`|メソッドが成功しましたが、スクリプトは、既に指定した状態にあった。|  
  
## <a name="remarks"></a>コメント  
 スクリプト エンジンの状態に関する詳細については、のスクリプト エンジンの状態を参照してください[Windows スクリプト エンジン](../../winscript/windows-script-engines.md)です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)