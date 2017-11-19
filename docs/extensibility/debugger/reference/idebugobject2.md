---
title: "IDebugObject2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2
helpviewer_keywords: IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6072d88bf6e065c7f9f72b5e6d1ffab0dcc46d03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、オブジェクトに関する追加情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、エイリアスとオブジェクトに関する情報へのアクセスのサポートを提供するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスを使用してこのインターフェイスを取得できます[QueryInterface](/cpp/atl/queryinterface)です。 また、 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイス、`IDebugObject2`インターフェイスは、次を実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|(存在する場合)、フィールドまたは変数を取得するオブジェクトによって表されるプロパティがバッキング可能性があります。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|このオブジェクトの値を表すマネージ コード オブジェクトを取得します。|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|このオブジェクトの一意の ID を作成または既存のエイリアスを取得します。|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|存在する場合は、このオブジェクトに関連付けられているエイリアスを取得します。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|このオブジェクトの種類を取得します。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|このオブジェクトがユーザー データを表すかどうかを判断します。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|エディット コンティニュの状態が無効になっているかどうかを判断します。<br /><br /> カスタム式エバリュエーターは、このメソッドを実装しない (常に返すか`E_NOTIMPL`)。|  
  
## <a name="remarks"></a>コメント  
 参照してください[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)エイリアスの詳細についてはします。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)