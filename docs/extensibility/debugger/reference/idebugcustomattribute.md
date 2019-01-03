---
title: IDebugCustomAttribute |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec02b9077108687b02e76db22f6349253bdbcb1f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841571"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
このインターフェイスは、カスタム属性を表し、名前、親、および属性の型のクラスを提供できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーは、シンボルに関連付けられているカスタム属性をサポートするために、このインターフェイスを実装します。 これは通常、独自のオブジェクトで実装されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[次](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)このインターフェイスを返します。 呼び出し、 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)メソッドが返す、 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugCustomAttribute`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|現在の属性がアタッチされているフィールドを取得します。|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|カスタム属性クラスの型を取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|カスタム属性の名前を取得します。|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|バイトの blob として属性情報を取得します。|  
  
## <a name="remarks"></a>Remarks  
 カスタム属性は、特定のクラスやメソッドに関連付けられているカスタム メタデータを提供する、c# の構造です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)