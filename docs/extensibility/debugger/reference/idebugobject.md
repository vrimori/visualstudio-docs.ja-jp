---
title: "IDebugObject | Microsoft Docs"
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
  - "IDebugObject"
helpviewer_keywords: 
  - "IDebugObject インターフェイス"
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、バインダーは、シンボルと式の値をカプセル化するを作成するオブジェクトを表します。  
  
## 構文  
  
```  
IDebugObject : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーターでは、オブジェクトを表すためには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 このインターフェイスは、式エバリュエーターが解析された式で使用するすべてのオブジェクトの基本クラスです。 呼び出しによって返される、 [バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md) メソッドです。[QueryInterface](/visual-cpp/atl/queryinterface) このインターフェイスより専門的なインターフェイスを取得します。  
  
## Vtable 順序のメソッド  
 次の表は、のメソッドを示しています。 `IDebugObject`します。  
  
|メソッド|説明|  
|----------|--------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|オブジェクトのサイズを取得します。|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|連続する一連のバイトとしてオブジェクトの値を取得します。|  
|[値の代入](../Topic/IDebugObject::SetValue.md)|連続する一連のバイトから、オブジェクトの値を設定します。|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|このオブジェクトの参照値を設定します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|オブジェクトの値のアドレスを表すメモリ コンテキストを取得します。|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|デバッグ エンジンのアドレス空間には、マネージ オブジェクトのコピーを作成します。|  
|[IsNullReference](../Topic/IDebugObject::IsNullReference.md)|このオブジェクトが null 参照であるかどうかをテストします。|  
|[IsEqual](../Topic/IDebugObject::IsEqual.md)|このオブジェクトを比較します。|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|このオブジェクトは読み取り専用のかどうかを判断します。|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|オブジェクトが、透過的プロキシであるかどうかを判断します。|  
  
## 解説  
 式エバリュエーターでは、基本クラスとしてこのインターフェイスを使用して、解析ツリー内のオブジェクトを表します。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../Topic/IDebugArrayObject::GetElement.md)   
 [バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)