---
title: "IActiveScriptProfilerCallback::ScriptCompiled |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
エンジン スクリプティング オブジェクト、スクリプトのコンパイルをプロファイラーに通知します。 このメソッドは、コンパイルされたすべてのスクリプトに対して呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `scriptId`  
 [in]コンパイルされたスクリプトの一意の ID。 この ID は、スクリプト エンジンによって割り当てられます。  
  
 `type`  
 [in]コンパイルされたスクリプトの種類。 値が定義されている[PROFILER_SCRIPT_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)です。  
  
 `pIDebugDocumentContext`  
 [in]場合へのポインター、`IUnknown`インターフェイスのクエリを実行する必要があります、プロファイラーを[IDebugDocumentContext インターフェイス](../../winscript/reference/idebugdocumentcontext-interface.md)ポインター。 それ以外の場合、これは null になります。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。  
  
## <a name="remarks"></a>コメント  
 これは、ホストでサポートされている場合にのみ、スクリプト エンジンではドキュメントのコンテキストを提供できます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)