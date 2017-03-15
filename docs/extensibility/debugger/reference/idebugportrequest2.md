---
title: "IDebugPortRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "IDebugPortRequest2 インターフェイス"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはポートについて説明します。  この説明はポートの仕入先にポートを追加するために使用されます。  
  
## 構文  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## 実装についてのメモ  
 Visual Studio はポートのサプライヤーからデバッグ ポートを取得するときに通常このインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このインターフェイスは [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) にデバッグ ポートを作成するために渡されます。  [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) の呼び出しは最初のポートを作成するために使用される要求を表すこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPortRequest2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|ポート名を作成するために取得します。|  
  
## 解説  
 デバッグ エンジンは通常サプライヤーのポートとやり取りしてこのインターフェイスに表示方向がありません。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)