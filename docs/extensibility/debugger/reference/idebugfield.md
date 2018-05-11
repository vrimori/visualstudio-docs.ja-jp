---
title: IDebugField |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2ff92f339568a6a20e2f85a0b2deae9c8db244f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfield"></a>IDebugField
このインターフェイスは、シンボルまたは型の説明は、フィールドを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーは、すべてのフィールドの基本クラスとして、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、すべてのフィールドの基本クラスです。 戻り値に基づく[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)、このインターフェイスを使用して複数の特殊なインターフェイスを返す可能性があります[QueryInterface](/cpp/atl/queryinterface)です。 さらに、多くのインターフェイスを返す`IDebugField`さまざまなメソッドからのオブジェクト。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugField`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|シンボルまたは型の表示可能な情報を取得します。|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|フィールドの種類を取得します。|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|フィールドの種類を取得します。|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|フィールドのコンテナーを取得します。|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|フィールドのアドレスを取得します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|(バイト単位)、フィールドのサイズを取得します。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|フィールドに関する情報を拡張を取得します。|  
|[等しいかどうか](../../../extensibility/debugger/reference/idebugfield-equal.md)|2 つのフィールドを比較します。|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|シンボルまたは型の型に依存しない情報を取得します。|  
  
## <a name="remarks"></a>コメント  
 型は C 言語に相当`typedef`です。  
  
 次の C++ 言語の例では`weather`、クラス型と`sunny`と`stormy`シンボルします。  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 フィールドは、シンボルを表すかどうか、または型を呼び出すことで決定できる[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)を調べること、 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)結果。 場合、`FIELD_KIND_TYPE`ビットが設定されている、このフィールドは、型と場合、`FIELD_KIND_SYMBOL`ビットが設定されているは、シンボル。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)