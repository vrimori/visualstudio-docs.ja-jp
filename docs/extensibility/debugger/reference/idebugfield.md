---
title: "IDebugField |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1e978ece2ecf56735dc538324b5c148f7f85b9bb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

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
