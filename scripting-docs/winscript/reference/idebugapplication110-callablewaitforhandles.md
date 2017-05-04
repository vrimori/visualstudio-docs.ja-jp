---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
このスレッドにポストされるように、スレッド間呼び出しの中に通知を送信する指定したハンドルのいずれかの待機時間。  このメソッドは、デバッガーのスレッドから呼び出す必要があります。  
  
> [!IMPORTANT]
>  [IDebugApplication110 インターフェイス](../../winscript/reference/idebugapplication110-interface.md) は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### パラメーター  
 `handleCount`  
 待機するハンドルの数。  
  
 `pHandles`  
 待機するハンドルのセット。  
  
 `pIndex`  
 HRESULT 値が S\_OK である場合、シグナル ハンドルの `pHandles` へのインデックス。  
  
## 参照  
 [IDebugApplication110 インターフェイス](../../winscript/reference/idebugapplication110-interface.md)