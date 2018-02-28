---
title: "IDebugPortSupplier2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 257bbf334adbdfd3a93cf172de0b15bf63cb3217
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
このインターフェイスは、セッションのデバッグ マネージャー (SDM) にポートを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート仕入先では、ポートのサプライヤーを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し`CoCreateInstance`ポート業者と`GUID`(これはこのインターフェイスを取得する一般的な方法です)、このインターフェイスを返します。 例:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 呼び出し[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)によって使用されている現在のポート仕入先を表す、このインターフェイスを返します[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]です。  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)ポートを作成したポート業者を表す、このインターフェイスを返します。  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)の一覧を表す`IDebugPortSupplier`インターフェイス (、`IEnumDebugPortSuppliers`インターフェイスがから取得した[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)に登録されているすべてのポートのサプライヤーを表す[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 デバッグ エンジン通常とは対話しませんポート業者です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPortSupplier2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|ポートの仕入先の名前を取得します。|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|ポートのサプライヤーの識別子を取得します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|ポートのサプライヤーからポートを取得します。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|既に存在するポートを列挙します。|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|ポート サプライヤーに新しいポートの追加がサポートされていることを確認します。|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|ポートを追加します。|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|ポートを削除します。|  
  
## <a name="remarks"></a>コメント  
 ポート サプライヤーできます名および ID によって識別される、および追加および削除ポート、ポート サプライヤーを提供するすべてのポートを列挙します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)