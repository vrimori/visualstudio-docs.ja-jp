---
title: "IDebugBreakpointRequest3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3"
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはブレークポイントの型を作成しバインドするために必要な情報を表します。  これは [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) の拡張です。  
  
## 構文  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## 実装についてのメモ  
 デバッグ セッションのマネージャーは \(SDM\)このインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 デバッグ エンジンは[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)\(DE\) に IDebugBreakpointRequest2 インターフェイスが受信する呼び出しの [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出してこのインターフェイスへのアクセス。  
  
## Vtable の順序でメソッド  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) から継承するメソッドに加え、`IDebugBreakpointRequest3` インターフェイスは次のメソッドを公開します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|このブレークポイントの要求を記述したブレークポイントの要求された情報を取得します。|  
  
## 解説  
 このインターフェイスは [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) の構造を通じて de\-DE に追加情報を提供するために使用されます。  この詳細についてはde\-DE の販売元の ID \(GUID の形式\)トレース ポイント名ブレークポイントの制約の名前が含まれます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)