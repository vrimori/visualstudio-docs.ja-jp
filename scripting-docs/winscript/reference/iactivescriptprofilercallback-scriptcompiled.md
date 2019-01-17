---
title: IActiveScriptProfilerCallback::ScriptCompiled |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf653e5623506a68e6353e3d9f97077592e87941
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091508"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
スクリプトのコンパイル、スクリプト エンジン オブジェクトをプロファイラーに通知します。 このメソッドは、コンパイルされたすべてのスクリプトに呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `scriptId`  
 [in]コンパイルされたスクリプトの一意の ID。 この ID は、スクリプト エンジンによって割り当てられます。  
  
 `type`  
 [in]コンパイルされたスクリプトの種類。 値が定義されている[PROFILER_SCRIPT_TYPE 列挙型](../../winscript/reference/profiler-script-type-enumeration.md)します。  
  
 `pIDebugDocumentContext`  
 [in]使用可能な場合へのポインター、`IUnknown`プロファイラーは次のクエリを実行する必要がありますインターフェイス、 [IDebugDocumentContext インターフェイス](../../winscript/reference/idebugdocumentcontext-interface.md)ポインター。 それ以外の場合、これは null になります。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。  
  
## <a name="remarks"></a>Remarks  
 これは、ホストでサポートされている場合にのみ、スクリプト エンジンは、ドキュメントのコンテキストを提供できます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerCallback インターフェイス](../../winscript/reference/iactivescriptprofilercallback-interface.md)