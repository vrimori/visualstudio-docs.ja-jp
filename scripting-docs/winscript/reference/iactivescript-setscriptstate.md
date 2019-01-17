---
title: Iactivescript::setscriptstate |Microsoft Docs
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
ms.openlocfilehash: 58edef17fec1d94a09b327dff626658c42a273ba
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095031"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
特定の状態には、スクリプト エンジンを設定します。 このメソッドは、ホスト オブジェクトまたはベース以外の吹き出しでベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイス。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ss`  
 [in]スクリプト エンジンを特定の状態に設定します。 定義されている値のいずれかを指定することができます、 [SCRIPTSTATE 列挙型](../../winscript/reference/scriptstate-enumeration.md)列挙体。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|スクリプト エンジンが初期化された状態に遷移をサポートしていません。 ホストする必要がありますこのスクリプト エンジンを破棄し、作成、初期化、および同じ効果を実現するために新しいスクリプト エンジンを読み込みます。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) し、そのために失敗しました。|  
|`OLESCRIPT_S_PENDING`|メソッドが正常にキューに登録が状態がまだ変更されていません。 ときに状態の変更、サイトはコールバックを通じて、 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)メソッド。|  
|`S_FALSE`|メソッドが成功しましたが、スクリプトが既に指定された状態。|  
  
## <a name="remarks"></a>Remarks  
 スクリプト エンジンの状態に関する詳細については、のスクリプト エンジンの状態を参照してください[Windows スクリプト エンジン](../../winscript/windows-script-engines.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Iactivescript::clone](../../winscript/reference/iactivescript-clone.md)   
 [Iactivescript::getscriptdispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [Iactivescript::interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [Iactivescriptparse::parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)