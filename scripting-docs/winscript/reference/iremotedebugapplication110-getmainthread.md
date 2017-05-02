---
title: "IRemoteDebugApplication110::GetMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetMainThread"
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IRemoteDebugApplication110::GetMainThread
呼び出す [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)ホストのメイン スレッドを返します。それ以外の場合は E\_FAIL を返します。  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md) は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
  
```  
  
#### パラメーター  
 `ppThread`  
 \[入力\]メイン [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)。  
  
## 参照  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 インターフェイス](../../winscript/reference/iremotedebugapplication110-interface.md)