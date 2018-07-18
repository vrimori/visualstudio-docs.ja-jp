---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd26ab1cf36378c0f037d78a3c079c58e004006d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727412"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
エンジンのスクリプト オブジェクトでは、ドキュメント オブジェクト モデル (DOM) の関数呼び出しの実行が完了をプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwszFunctionName`  
 [in]スクリプト エンジンが実行を完了したこと、関数の名前。  
  
 `scriptType`  
 [in]関数の型。 有効な値の詳細については、次を参照してください。 [PROFILER_SCRIPT_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。  
  
## <a name="remarks"></a>コメント  
 DOM の呼び出しのため、スクリプト エンジンでは呼び出す代わりにこのメソッドを呼び出します[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)です。 これは DOM の一意のメソッドおよびプロパティの数が多いため、します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 インターフェイス](../../winscript/reference/iactivescriptprofilercallback2-interface.md)