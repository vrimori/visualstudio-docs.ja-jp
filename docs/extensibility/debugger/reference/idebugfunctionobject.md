---
title: "IDebugFunctionObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject"
helpviewer_keywords: 
  - "IDebugFunctionObject インターフェイス"
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、関数を表します。  
  
## 構文  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## 実装についてのメモ  
 式エバリュエーターでは、関数を表すためには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 このインターフェイスは、特殊化した、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) インターフェイスし、使用して取得 [QueryInterface](/visual-cpp/atl/queryinterface) 上、 `IDebugObject` インターフェイスです。  
  
## Vtable 順序のメソッド  
 継承されたメソッドだけでなく [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), 、 `IDebugFunctionObject` インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|プリミティブ データ オブジェクトを作成します。|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|コンス トラクターを使用してオブジェクトを作成します。|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|コンス トラクターがないと、オブジェクトを作成します。|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|配列オブジェクトを作成します。|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|文字列オブジェクトを作成します。|  
|[評価します。](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|関数の呼び出しをオブジェクトとして結果の値を返します。|  
  
## 解説  
 このインターフェイスには、解析ツリー内の関数を表すため、式エバリュエーターが有効です。`Create` このインターフェイスでメソッドを使用して、メソッドへの入力パラメーターを表すオブジェクトを構築します。 呼び出して、この関数を実行し、ことができます、 [評価します。](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) メソッドで、関数の戻り値を表すオブジェクトを返します。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)