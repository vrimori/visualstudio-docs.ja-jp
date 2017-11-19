---
title: "IActiveScriptProfilerCallback::Shutdown |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
スクリプト エンジンでプロファイリングを停止するたびに、プロファイラーのオブジェクトを通知するために呼び出されます。 これにより、必要な場合、プロファイラーのオブジェクトでそのクリーンアップ ルーチンを呼び出すことができます。 スクリプト エンジンのシャット ダウン時またはへの呼び出し時に、このメソッドは、スクリプト エンジンによって呼び出されます[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)は失敗します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hrReason`  
 [in]シャット ダウンの理由です。 場合は、スクリプト エンジンのシャット ダウン`S_OK`が渡されます。 場合への呼び出し[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)失敗を示す HRESULT を返します、HRESULT が渡されます。 この値を取得する場合は、 [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)