---
title: PROFILER_EVENT_MASK 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da55371c24f6a21acbc9dc789a2c76ef6e7c66b4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096669"
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK 列挙型
プロファイルが必要なイベントの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|ユーザーが記述したスクリプトと動的なコードで定義されている関数をプロファイルします。|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|スクリプト エンジンによって定義されているネイティブ関数をプロファイルします。|  
|PROFILER_EVENT_MASK_TRACE_ALL|ドキュメント オブジェクト モデル (DOM) に呼び出しを除く、すべてのユーザー定義とスクリプト エンジン関数をプロファイルします。|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|DOM への呼び出しのプロファイル関数|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|DOM への呼び出しを含む、すべての関数をプロファイルします。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト Profiler の定数、列挙型および構造体](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)