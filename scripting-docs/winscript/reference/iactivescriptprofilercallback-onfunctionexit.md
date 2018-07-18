---
title: IActiveScriptProfilerCallback::OnFunctionExit |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57a3343c7e3747c48a4c43a1c1ac17fe6502aee3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724692"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
オブジェクト、スクリプト エンジンで関数の実行が完了を呼び出すことがないことにドキュメント オブジェクト モデル (DOM) の呼び出しをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `scriptId`  
 [in]一部は、関数は、スクリプトの一意の ID。 この ID は、スクリプト エンジンによって割り当てられます。  
  
 `functionId`  
 [in]関数の一意の ID。 この ID は、スクリプト エンジンによって割り当てられます。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。  
  
## <a name="remarks"></a>コメント  
 スクリプト エンジンを呼び出し、DOM の呼び出し、 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)の代わりに`IActiveScriptProfilerCallback::OnFunctionExit`です。 これは DOM の一意のメソッドおよびプロパティの数が多いため、します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)