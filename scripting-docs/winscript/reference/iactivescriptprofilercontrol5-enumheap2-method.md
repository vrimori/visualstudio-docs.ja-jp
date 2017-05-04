---
title: "IActiveScriptProfilerControl5::EnumHeap2 メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerControl5::EnumHeap2 メソッド
関連付けられたスクリプト エンジンのコンテキストで GC ヒープ オブジェクトを繰り返すために使用できるインターフェイス \([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) を返します。  
  
 デバッグ モードまたはリリース モードでこのメソッドを呼び出すことができます。  このメソッドは、UI スレッドがアイドル状態のときに呼び出す必要があります。  メソッドが呼び出された後、[IActiveScriptProfilerHeapEnum::Next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) が S\_FALSE を返すか、[IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) インターフェイス ポインターが解放されるまでは、[IActiveScriptProfilerHeapEnum::Next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 以外のスクリプト エンジンに対して操作を実行することはできません。  
  
## 構文  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### パラメーター  
 enumFlags  
 オブジェクト リレーションシップ内でオブジェクトが指すものに関する補足情報を、公開するかどうかを指定する値です。  補足情報は、オブジェクトが Getter または Setter メソッドを指しているかを表す可能性があります。  詳細については、「[PROFILER\_HEAP\_ENUM\_FLAGS 列挙型](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)」を参照してください。  
  
 ppEnum  
 \[出力\] [IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) を返します。  
  
## 戻り値  
 HRESULT を返します。  次の値を指定できます。  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|ヒープ列挙は正常に完了しました。|  
|`E_OUTOFMEMORY`|ヒープ列挙を実行するのに十分なメモリがありませんでした。|  
|`E_FAIL`|内部エラーが発生しました。|