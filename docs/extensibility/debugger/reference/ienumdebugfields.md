---
title: "IEnumDebugFields | Microsoft Docs"
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
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "IEnumDebugFields インターフェイス"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスを実装するオブジェクトのコレクションを表します。  
  
## 構文  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはシンボルのプロバイダーによって [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスを実装するオブジェクトを指定するために実装されます。  これは [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) のメソッドが存在すると標準の COM 列挙型ではないことに注意してください。  
  
## 呼び出し元のメモ  
 このインターフェイスは [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md) と [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md) によって返されます。  
  
## Vtable の順序でメソッド  
 このインターフェイスは以下のメソッドを実装します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|列挙体から [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のオブジェクトのセットを取得します。|  
|[Skip](../Topic/IEnumDebugFields::Skip.md)|エントリの指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|最初のエントリに列挙をリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|現在の列挙体のコピーを取得します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|列挙エントリの数を取得します。|  
  
## 解説  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)