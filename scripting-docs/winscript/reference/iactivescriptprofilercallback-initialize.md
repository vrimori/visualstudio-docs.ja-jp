---
title: IActiveScriptProfilerCallback::Initialize |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82e599ae94f422352706a0ec6cd9387bfa6799f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724412"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
スクリプト エンジンでプロファイリングが開始されるたびに、プロファイラーのオブジェクトを初期化するために呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwContext`  
 [in]渡される 4 バイト値[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)です。  
  
## <a name="return-value"></a>戻り値  
 HRESULT を返します。 次の値を指定できます。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 メソッドは、プロファイラーのオブジェクトを初期化できない場合、は、スクリプト エンジンに通知するエラー HRESULT を返します。 この場合、スクリプト エンジンを呼び出す必要があります直接[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)HRESULT をパラメーターに渡して、プロファイラーのオブジェクトを解放します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)