---
title: "IDebugPointerObject3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPointerObject3 インターフェイス"
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPointerObject3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 解析ツリー内のポインターを表し、拡張、 **IDebugPointerObject** インターフェイスです。  
  
## 構文  
  
```  
IDebugPointerObject3 : IDebugPointerObject  
```  
  
## 実装についてのメモ  
 式エバリュエーター \(EE\) では、このインターフェイスを実装します。  
  
## メソッド  
 上のメソッドだけでなく、 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|----------|--------|  
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|ポインターのアドレスを取得します。|  
  
## 必要条件  
 ヘッダー: Ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll