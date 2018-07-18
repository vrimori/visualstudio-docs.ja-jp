---
title: IActiveScriptSite::OnScriptTerminate |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724802"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
スクリプトの実行が完了したことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvarResult`  
 [in]スクリプトの結果を格納する変数のアドレスまたは`NULL`場合は、スクリプトに結果が生成されません。  
  
 `pexcepinfo`  
 [in]アドレス、`EXCEPINFO`スクリプトが終了した場合に生成された例外情報を格納する構造体または`NULL`例外が生成されない場合。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## <a name="remarks"></a>コメント  
 スクリプト エンジンが呼び出しの前に、このメソッドを呼び出して、 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 、SCRIPTSTATE_INITIALIZED フラグを設定して、メソッドが完了します。 このメソッドは、ホストに完了の状態と結果を返しますを使用できます。 基づくホストからイベントをシンク、多くのスクリプト言語がホストによって定義されている有効期限があることに注意してください。 この場合、このメソッドは呼び出すことはありません。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)