---
title: "IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IDebugApplicationThread110::AsynchronousCallIntoThread
メイン スレッドで非同期呼び出しを行います。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 インターフェイス](../../winscript/reference/idebugapplicationthread110-interface.md) は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
  
```  
  
#### パラメーター  
 `pptc`  
 への呼び出し [IDebugThreadCall インターフェイス](../../winscript/reference/idebugthreadcall-interface.md) のオブジェクト。  
  
 `dwParam1`  
 呼び出しの最初のパラメーター。  
  
 `dwParam1`  
 呼び出しの最初のパラメーター。  
  
 `dwParam2`  
 呼び出しの 2 番目のパラメーター。  
  
 `dwParam3`  
 呼び出しの 3 番目のパラメーター。  
  
## 参照  
 [IDebugApplication110 インターフェイス](../../winscript/reference/idebugapplication110-interface.md)