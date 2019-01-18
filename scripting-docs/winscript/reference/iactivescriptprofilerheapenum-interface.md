---
title: IActiveScriptProfilerHeapEnum インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14562654e0fd3f3567d6f598f84cf2c966b1b8cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344890"
---
# <a name="iactivescriptprofilerheapenum-interface"></a>IActiveScriptProfilerHeapEnum インターフェイス
反復子、ヒープ上のオブジェクトによって収集された、スクリプト エンジンに関連付けられた、 [iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 [IActiveScriptProfilerHeapEnum::Next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 によって収集されたヒープ オブジェクトのセット内の次のオブジェクトまたはオブジェクトの取得、 [iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)します。  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 によって収集されたヒープ オブジェクトのセットの指定したオブジェクトの省略可能な情報を取得、 [iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)します。  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 指定した解放[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)構造とそれに関連付けられた[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)要素。  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 対応する文字列名を返します[PROFILER_HEAP_OBJECT_NAME_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)値.