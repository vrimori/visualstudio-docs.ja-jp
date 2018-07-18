---
title: PROFILER_SCRIPT_TYPE 列挙型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734122"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE 列挙型
スクリプトの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|ユーザーが記述したスクリプト コードを指定します。|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|実行中に動的に生成されるスクリプト コードを指定します。|  
|PROFILER_SCRIPT_TYPE_NATIVE|ネイティブ関数とスクリプト エンジンが定義されているオブジェクトのスクリプトの種類を指定します。|  
|PROFILER_SCRIPT_TYPE_DOM|呼び出しに、ドキュメント オブジェクト モデル (DOM)、Internet Explorer への呼び出しなどの指定、`document.getElementById`メソッドです。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト プロファイラーの定数、列挙型および構造体](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)