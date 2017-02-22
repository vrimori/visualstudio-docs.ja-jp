---
title: "IDebugArrayObject | Microsoft Docs"
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
  - "IDebugArrayObject"
helpviewer_keywords: 
  - "IDebugArrayObject メソッド"
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、配列オブジェクトを表します。  
  
## 構文  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## 実装についてのメモ  
 式エバリュエーターでは、配列を表すためには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) インターフェイスを使用してこのインターフェイスを取得できる [QueryInterface](/visual-cpp/atl/queryinterface) 場合は、オブジェクトが配列を表します。  
  
## Vtable 順序のメソッド  
 上のメソッドだけでなく、 `IDebugObject` 、次のメソッドが実装されているインターフェイス、 `IDebugArrayObject` インターフェイスです。  
  
|メソッド|説明|  
|----------|--------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|配列の要素の数を取得します。|  
|[GetElement](../Topic/IDebugArrayObject::GetElement.md)|配列の要素を取得します。|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|配列のすべての要素を取得します。|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|配列のランクを取得します。|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|配列の次元を取得します。|  
  
## 解説  
 式エバリュエーターでは、このインターフェイスを使用して、解析ツリー内の配列を表します。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)