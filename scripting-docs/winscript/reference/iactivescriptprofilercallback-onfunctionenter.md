---
title: IActiveScriptProfilerCallback::OnFunctionEnter |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 887810d12a20045c95b0f837db1592b9b7bf301e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095382"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
ドキュメント オブジェクト モデル (DOM) への呼び出しではない関数呼び出しの実行を開始するスクリプト エンジンは、プロファイラーのオブジェクトに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `scriptId`  
 [in]スクリプトの一部では、関数の一意の ID。 この ID は、スクリプト エンジンによって割り当てられます。  
  
 `functionId`  
 [in]関数の一意の ID。 この ID は、スクリプト エンジンによって割り当てられます。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。  
  
## <a name="remarks"></a>Remarks  
 スクリプト エンジンの呼び出し、DOM 呼び出し[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)の代わりに`IActiveScriptProfilerCallback::OnFunctionEnter`します。 これは一意のメソッドと DOM のプロパティの数が多いためです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)