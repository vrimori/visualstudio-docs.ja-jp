---
title: "IActiveScriptProfilerControl3::EnumHeap メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl3::EnumHeap メソッド
関連のスクリプト エンジンのコンテキストで GC ヒープのオブジェクトを反復処理するために使用できるインターフェイス \([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) を返します。  
  
 デバッグでこのメソッドを呼び出すか、またはモードを解放できます。  このメソッドは、UI スレッドがアイドル状態のときに呼び出されます。  メソッドが呼び出された後、操作は [IActiveScriptProfilerHeapEnum::Next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) を除き、スクリプト エンジンに対して [IActiveScriptProfilerHeapEnum::Next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) は S\_FALSE を返すか、または [IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) のインターフェイス ポインターが解放されるまで実行する必要ではありません。  
  
## 構文  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### パラメーター  
 ppEnum  
 \[出力\] [IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) を返します。  
  
## 戻り値  
 HRESULT。