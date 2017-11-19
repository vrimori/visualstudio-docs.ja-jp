---
title: "PROFILER_EVENT_MASK 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68547fcb1fd2cd34b18a3d204baefd24d9da936b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK 列挙型
プロファイルが必要なイベントの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```  
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
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|ユーザーが記述したスクリプトと動的なコードで定義されているプロファイル機能です。|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|スクリプト エンジンが定義されているネイティブ関数をプロファイルします。|  
|PROFILER_EVENT_MASK_TRACE_ALL|呼び出しにドキュメント オブジェクト モデル (DOM) を除く、およびユーザー定義のスクリプト エンジンのすべての機能をプロファイルします。|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|DOM への呼び出しをプロファイル関数|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|DOM への呼び出しを含む、すべての関数をプロファイルします。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーの定数、列挙型および構造体](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)