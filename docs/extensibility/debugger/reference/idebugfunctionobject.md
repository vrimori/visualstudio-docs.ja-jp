---
title: IDebugFunctionObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d352870800a7b5e7fc1408d607a24f616b0f22d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954170"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、関数を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、関数を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、特殊化した、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスを使用して取得[QueryInterface](/cpp/atl/queryinterface)上、`IDebugObject`インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)、`IDebugFunctionObject`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|プリミティブ データ オブジェクトを作成します。|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|コンス トラクターを使用してオブジェクトを作成します。|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|なしのコンス トラクターを持つオブジェクトを作成します。|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|配列オブジェクトを作成します。|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|文字列オブジェクトを作成します。|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|関数の呼び出しをオブジェクトとして結果の値を返します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、解析ツリー内の関数を表す式エバリュエーターを使用します。 `Create`メソッドへの入力パラメーターを表すオブジェクトを構築するこのインターフェイスのメソッドを使用します。 関数を呼び出すことによって実行できます、 [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)メソッドで、関数の戻り値を表すオブジェクトを返します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)