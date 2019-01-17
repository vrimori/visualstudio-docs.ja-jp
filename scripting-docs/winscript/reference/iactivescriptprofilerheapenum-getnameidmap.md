---
title: IActiveScriptProfilerHeapEnum::GetNameIdMap |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdff1983524b9234d536a23378d300a0b815522d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092639"
---
# <a name="iactivescriptprofilerheapenumgetnameidmap"></a>IActiveScriptProfilerHeapEnum::GetNameIdMap
対応する文字列名を返します[PROFILER_HEAP_OBJECT_NAME_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)値。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetNameIdMap (    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],     [out] UINT *pcelt);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pNameList`  
 [out]関連付けられている名前の配列[PROFILER_HEAP_OBJECT_NAME_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)値。  
  
 `pcelt`  
 [out]配列内の名前の数。  
  
## <a name="return-value"></a>戻り値  
 HRESULT。