---
title: IDebugArrayObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c101433bf561ccb6d21e8fcb7e3ea1bb1148eebd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822114"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、配列オブジェクトを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、配列を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスを使用してこのインターフェイスを取得できる[QueryInterface](/cpp/atl/queryinterface)場合は、オブジェクトの配列を表します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 `IDebugObject` 、次のメソッドが実装されている、インターフェイス、`IDebugArrayObject`インターフェイス。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|配列内の要素数を取得します。|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|配列の要素を取得します。|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|配列のすべての要素を取得します。|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|配列のランクを取得します。|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|配列の次元を取得します。|  
  
## <a name="remarks"></a>Remarks  
 式エバリュエーターでは、このインターフェイスを使用して、解析ツリー内の配列を表します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)