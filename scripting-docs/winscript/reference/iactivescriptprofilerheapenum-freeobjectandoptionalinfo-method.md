---
title: Iactivescriptprofilerheapenum::freeobjectandoptionalinfo メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dd2b827deba31af1958842cf0dacd2a85f4260d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095694"
---
# <a name="iactivescriptprofilerheapenumfreeobjectandoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo メソッド
指定した解放[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)構造とそれに関連付けられた[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)要素。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT FreeObjectAndOptionalInfo (    [in] ULONG celt,    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 解放するオブジェクトの数。  
  
 `heapObjects`  
 配列の[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)構造体。  
  
## <a name="return-value"></a>戻り値  
 HRESULT。