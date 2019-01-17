---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName |Microsoft Docs
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
ms.openlocfilehash: fb198f56e5ff73561fe7b42a25b019dfb0e3817c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094563"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
スクリプト エンジン オブジェクトは、ドキュメント オブジェクト モデル (DOM) の関数呼び出しの実行が完了をプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwszFunctionName`  
 [in]スクリプト エンジンが実行を終了したこと、関数の名前。  
  
 `scriptType`  
 [in]関数の型。 有効な値の説明については、次を参照してください。 [PROFILER_SCRIPT_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。  
  
## <a name="remarks"></a>Remarks  
 DOM の呼び出しは、スクリプト エンジンは呼び出す代わりに、このメソッドを呼び出します。 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)します。 これは一意のメソッドと DOM のプロパティの数が多いためです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 インターフェイス](../../winscript/reference/iactivescriptprofilercallback2-interface.md)