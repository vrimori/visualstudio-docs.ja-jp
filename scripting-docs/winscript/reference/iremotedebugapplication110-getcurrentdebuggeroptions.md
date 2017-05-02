---
title: "IRemoteDebugApplication110::GetCurrentDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetCurrentDebuggerOptions"
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::GetCurrentDebuggerOptions
現在有効になっているオプションのセットを返します。  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md) は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### パラメーター  
 `pCurrentOptions`  
 \[入力\]現在の選択。  
  
## 参照  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 インターフェイス](../../winscript/reference/iremotedebugapplication110-interface.md)