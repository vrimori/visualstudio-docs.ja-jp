---
title: Iactivescriptprofilercontrol 5::enumheap2 メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724662"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 メソッド
インターフェイスを返します ([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) を使用して、関連付けられているスクリプト エンジンのコンテキストで GC ヒープのオブジェクトを反復処理をすることができます。  
  
 デバッグ モードまたはリリース モードでこのメソッドを呼び出すことができます。 このメソッドは、UI スレッドがアイドル状態のときに呼び出す必要があります。 メソッドが呼び出された後の操作に対して実行してくださいありませんを除く、スクリプト エンジン[iactivescriptprofilerheapenum::next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)まで[iactivescriptprofilerheapenum::next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)S_FALSE を返しますまたは、 [IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)インターフェイス ポインターを解放します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>パラメーター  
 enumFlags  
 オブジェクト リレーションシップ内でオブジェクトが指すものに関する補足情報を、公開するかどうかを指定する値です。 補足情報は、オブジェクトが Getter または Setter メソッドを指しているかを表す可能性があります。 詳細については、次を参照してください。 [PROFILER_HEAP_ENUM_FLAGS 列挙型](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)です。  
  
 ppEnum  
 [out]返します、 [IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)です。  
  
## <a name="return-value"></a>戻り値  
 HRESULT を返します。 次の値を指定できます。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|ヒープ列挙は正常に完了しました。|  
|`E_OUTOFMEMORY`|ヒープ列挙を実行するのに十分なメモリがありませんでした。|  
|`E_FAIL`|内部エラーが発生しました。|