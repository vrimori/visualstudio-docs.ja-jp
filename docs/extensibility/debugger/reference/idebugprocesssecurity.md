---
title: "IDebugProcessSecurity | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity インターフェイス"
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`IDebugProcessSecurity` はポートの仕入先によってプロセスへのアタッチが安全であることをユーザーに通知するために実装されます。  
  
## 構文  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProcessSecurity` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|ポートのサプライヤーからユーザー名を取得します。|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|デバッグ プロセスへのアタッチが安全でないユーザーに警告します。|  
  
## 解説  
 アタッチするプロセスが安全と見なされる可能性がある場合に警告を表示しユーザーをキャンセルできるようにこのインターフェイスを実装します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [ポート](../../../extensibility/debugger/ports.md)   
 [ポートの仕入先](../../../extensibility/debugger/port-suppliers.md)   
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)