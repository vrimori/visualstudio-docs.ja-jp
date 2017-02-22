---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFirewallConfigurationCallback2 インターフェイス"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] の UI を呼び出すためにファイアウォールがリモート デバッグをブロックするために DCOM が使用するデバッグ エンジンを有効にします。  
  
## 構文  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ セッションのマネージャーのポートのオブジェクトによって実装されます。  
  
## メソッド  
 次の表は `IDebugFirewallConfigurationCallback2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|要求にファイアウォールをブロックしないリモート デバッグします。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll