---
title: IDebugField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1b4b7f27bbecd71fa5a99e942d5f1b75e983c0d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002483"
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
 このインターフェイスは、すべてのフィールドの基本クラスです。 戻り値に基づく[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)、このインターフェイスを使用してより専門的なインターフェイスを返す可能性があります[QueryInterface](/cpp/atl/queryinterface)します。 さらに、多くのインターフェイスを返す`IDebugField`さまざまなメソッドからのオブジェクト。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugField`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|シンボルまたは型の表示可能な情報を取得します。|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|フィールドの種類を取得します。|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|フィールドの型を取得します。|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|フィールドのコンテナーを取得します。|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|フィールドのアドレスを取得します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|(バイト単位)、フィールドのサイズを取得します。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|拡張フィールドに関する情報を取得します。|  
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|2 つのフィールドを比較します。|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|シンボルまたは型に関する型に依存しない情報を取得します。|  
  
## <a name="remarks"></a>Remarks  
 型は C 言語に相当`typedef`します。  
  
 C++ 言語の次の例で`weather`はクラス型、および`sunny`と`stormy`シンボルします。  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 フィールド シンボルを表すかどうか、または型を呼び出すことで決定できる[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)を調べて、 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)結果。 場合、`FIELD_KIND_TYPE`ビットが設定されて、フィールド型の場合は、場合に、`FIELD_KIND_SYMBOL`ビットが設定されて、シンボル。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)