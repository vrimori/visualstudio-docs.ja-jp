---
title: "IEnumDebugAddresses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "IEnumDebugAddresses インターフェイス"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) のインターフェイスを実装するオブジェクトのコレクションを表します。  
  
## 構文  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはシンボルのプロバイダーによって [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) のインターフェイスを実装するオブジェクトを指定するために実装されます。  これは [GetCount](../Topic/IEnumDebugAddresses::GetCount.md) のメソッドが存在すると標準の COM 列挙型ではないことに注意してください。  
  
## 呼び出し元のメモ  
 このインターフェイスは [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) と [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md) によって返されます。  
  
## Vtable の順序でメソッド  
 このインターフェイスは以下のメソッドを実装します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../Topic/IEnumDebugAddresses::Next.md)|列挙体から [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) のオブジェクトのセットを取得します。|  
|[Skip](../Topic/IEnumDebugAddresses::Skip.md)|エントリの指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|最初のエントリに列挙をリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|現在の列挙体のコピーを取得します。|  
|[GetCount](../Topic/IEnumDebugAddresses::GetCount.md)|列挙エントリの数を取得します。|  
  
## 解説  
 適切なアドレスを確認するには式エバリュエーターにするにはデバッグ エンジンによってこのインターフェイスがよく使用されます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)