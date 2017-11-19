---
title: "Iactivescriptprofilerheapenum::getoptionalinfo メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo メソッド
指定したオブジェクトの省略可能な情報を取得します (から返されるヒープ オブジェクトのセットから、 [iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md))。  
  
 返されたオブジェクトに割り当てられている返されたメモリを解放する必要はありません。 代わりを呼び出す必要があります、 [iactivescriptprofilerheapenum::freeobjectandoptionalinfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `heapObject`  
 [PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)情報を取得します。  
  
 `celt`  
 数[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)構造体を返します。  
  
 `optionalInfo`  
 [out]配列[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)指定したオブジェクトの構造体。  
  
## <a name="return-value"></a>戻り値  
 HRESULT。