---
title: IActiveScriptProfilerControl::StartProfiling |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5540573991be11230acb33b088174bbb5c39f7f7
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281716"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
スクリプト エンジンのプロファイリングを開始します。 スクリプト エンジンを呼び出すことによって、プロファイラー オブジェクトのインスタンスを作成する[CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)します。  
  
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
 [in]イベントの種類を指定する 4 バイトのビットマスク。 ビットが定義されている[PROFILER_EVENT_MASK 列挙型](../../winscript/reference/profiler-event-mask-enumeration.md)します。  
  
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