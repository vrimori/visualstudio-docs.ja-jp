---
title: IDebugObject2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f12376cfeb416b48278f340081fa334a8acdbfc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834706"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、オブジェクトに関する追加情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、エイリアスとオブジェクトに関する情報へのアクセスのサポートを提供するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスを使用してこのインターフェイスを取得できる[QueryInterface](/cpp/atl/queryinterface)します。 また、 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 メソッドだけでなく、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイス、`IDebugObject2`インターフェイスは、次を実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|フィールドまたは変数を取得します (ある場合) をこのオブジェクトによって表されるプロパティをサポートする場合があります。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|このオブジェクトの値を表すマネージ コード オブジェクトを取得します。|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|このオブジェクトの一意の ID を作成します。 または、既存のエイリアスを取得します。|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|存在する場合、このオブジェクトに関連付けられているエイリアスを取得します。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|このオブジェクトの型を取得します。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|このオブジェクトがユーザー データを表すかどうかを判断します。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|エディット コンティニュの状態が無効になっているかどうかを判断します。<br /><br /> カスタム式エバリュエーターは、このメソッドを実装しない (常に返すことは`E_NOTIMPL`)。|  
  
## <a name="remarks"></a>Remarks  
 参照してください[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)エイリアスの詳細についてはします。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)