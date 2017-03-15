---
title: "IDebugAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress"
helpviewer_keywords: 
  - "IDebugAddress インターフェイス"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは項目のアドレスを表します。  これはシンボル ハンドラーによって返されます。  
  
## 構文  
  
```  
IDebugAddress : IUnknown  
```  
  
## 実装についてのメモ  
 シンボルのプロバイダーはオブジェクトのアドレスを表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 多くのインターフェイスのメソッドはこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 このインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|オブジェクトと場所を示す [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) の構造体を取得します。|  
  
## 解説  
 シンボルのプロバイダーは特定のスコープ内のオブジェクトと位置を表すためこのインターフェイスを返します \(たとえば関数メソッドまたはクラス\)。  このインターフェイスはから戻りシンボルのプロバイダーと式エバリュエーターのさまざまなメソッドに渡されます。  通常シンボルのプロバイダーでこのインターフェイスの内容を解釈する必要があるのエンティティです。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)