---
title: "IActiveScriptProfilerControl::StartProfiling |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5362eaba439ff7a645a8323c4eed5d9496f6d88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
スクリプト エンジンでプロファイリングを開始します。 スクリプト エンジンでは、プロファイラーのオブジェクトのインスタンスを作成を呼び出すことによって[CoCreateInstance](http://msdn.microsoft.com/en-us/7295a55b-12c7-4ed0-a7a4-9ecee16afdec)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `clsidProfilerObject`  
 [in]クラス id (CLSID) プロファイラー オブジェクトを作成します。  
  
 `dwEventMask`  
 [in]イベントの種類を指定する 4 バイトのビットマスク。 Bits が定義されている[PROFILER_EVENT_MASK 列挙型](../../winscript/reference/profiler-event-mask-enumeration.md)です。  
  
 `dwContext`  
 [in]プロファイラーのオブジェクトに渡される 4 バイト値。  
  
## <a name="return-value"></a>戻り値  
 HRESULT を返します。 次の値を指定できます。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|メソッドが成功しました。|  
|`ACTIVPROF_E_PROFILER_PRESENT`|プロファイルは既に有効です。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerControl インターフェイス](../../winscript/reference/iactivescriptprofilercontrol-interface.md)