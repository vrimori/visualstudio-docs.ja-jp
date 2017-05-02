---
title: "IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsSuspendedForBreakPoint"
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsSuspendedForBreakPoint
[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) がこのスレッドで呼び出される判断し、まだ完了しているかどうかがありません。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 インターフェイス](../../winscript/reference/idebugapplicationthread110-interface.md) は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### パラメーター  
 `pfIsSuspended`  
 \[入力\]スレッドがブレークポイントで中断された場合 `true`、それ `false`。  
  
## 参照  
 [IDebugApplicationThread110 インターフェイス](../../winscript/reference/idebugapplicationthread110-interface.md)