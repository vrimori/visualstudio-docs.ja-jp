---
title: "IActiveScriptProfilerHeapEnum インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4761e8c7d4cc9c3372c7906e1503b8dbd059ca33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenum-interface"></a>IActiveScriptProfilerHeapEnum インターフェイス
ヒープを指す反復子オブジェクトによって収集された、スクリプト エンジンと関連付けられている、 [iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 [IActiveScriptProfilerHeapEnum::Next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 によって収集されたヒープのオブジェクトのセット内の次のオブジェクトまたはオブジェクトを取得、 [iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)です。  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 によって収集されたヒープのオブジェクトのセット内の指定したオブジェクトのオプションの情報を取得、 [iactivescriptprofilercontrol 3::enumheap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)です。  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo メソッド](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 指定した解放[PROFILER_HEAP_OBJECT 構造体](../../winscript/reference/profiler-heap-object-structure.md)構造とそれに関連付けられた[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 構造体](../../winscript/reference/profiler-heap-object-optional-info-structure.md)要素。  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 対応する文字列名を返します[PROFILER_HEAP_OBJECT_NAME_ID 型](../../winscript/reference/profiler-heap-object-name-id-type.md)値.