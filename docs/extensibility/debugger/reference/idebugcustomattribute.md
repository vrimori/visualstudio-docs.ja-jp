---
title: "IDebugCustomAttribute |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute
helpviewer_keywords: IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48aeab8a09d4916c31c5e2b781427988cf352b25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
このインターフェイスは、カスタム属性を表すし、名前、親、および属性のクラス型を提供できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーは、シンボルに関連付けられているカスタム属性をサポートするために、このインターフェイスを実装します。 これは通常、独自のオブジェクトで実装されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[次](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)このインターフェイスを返します。 呼び出し、 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)メソッドを返します、 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugCustomAttribute`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|現在の属性が関連付けられているフィールドを取得します。|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|カスタム属性クラスの型を取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|カスタム属性の名前を取得します。|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|バイトの blob として属性情報を取得します。|  
  
## <a name="remarks"></a>コメント  
 カスタム属性は、C# の場合、特定のクラスまたはメソッドに関連付けられているカスタムのメタデータを提供する構造です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [シンボル プロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)