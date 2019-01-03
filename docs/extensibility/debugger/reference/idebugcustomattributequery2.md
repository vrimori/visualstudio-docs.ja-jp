---
title: IDebugCustomAttributeQuery2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5c71c8a8820a76eb0f3784aaf899f05f48a76e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836375"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
このフィールドのカスタム属性の存在を定義し、存在する場合は、属性の情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーを実装する同一のオブジェクトにこのインターフェイスを実装する[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)カスタム属性をサポートするためにします。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用[QueryInterface](/cpp/atl/queryinterface)からこのインターフェイスを取得する、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの**IDebugCustomAttributeQuery**インターフェイス。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|名前でカスタム属性が存在するかどうかを判断します。|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|指定されたカスタム属性の属性情報を取得します。|  
  
 加え、 **IDebugCustomAttributeQuery**メソッド、`IDebugCustomAttributeQuery2`次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|このフィールドにアタッチされているすべてのカスタム属性の列挙子を取得します。|  
  
## <a name="remarks"></a>Remarks  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)メソッドは、このフィールドに対して定義されているすべてのカスタム属性の列挙子を返すことができます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)