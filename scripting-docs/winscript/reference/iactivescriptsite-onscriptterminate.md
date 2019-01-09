---
title: IActiveScriptSite::OnScriptTerminate |Microsoft Docs
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
ms.openlocfilehash: f8ff7c3d531b46fa6681776e79fbb73f6d1efca2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087114"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
スクリプトの実行が完了したことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvarResult`  
 [in]スクリプトの結果を格納する変数のアドレスまたは`NULL`場合は、スクリプトに結果が生成されません。  
  
 `pexcepinfo`  
 [in]アドレス、`EXCEPINFO`スクリプトが終了したときに生成された例外情報を格納する構造または`NULL`例外が生成されない場合。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## <a name="remarks"></a>Remarks  
 スクリプト エンジンは、呼び出しの前に、このメソッドを呼び出して、 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 、SCRIPTSTATE_INITIALIZED フラグを設定して、メソッドが完了しました。 完了の状態と結果をホストに戻るには、このメソッドを使用できます。 ホストからのシンク イベントに基づき、多くのスクリプト言語が、ホストで定義されている有効期限があることに注意してください。 この場合、このメソッドが呼び出されない場合があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)