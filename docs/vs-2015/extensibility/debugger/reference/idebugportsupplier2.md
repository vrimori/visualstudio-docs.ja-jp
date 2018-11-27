---
title: IDebugPortSupplier2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2e992061fa3486f179e3f498846e0f18b8c1598
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785132"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスには、セッション デバッグ マネージャー (SDM) へのポートが用意されています。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート サプライヤーは、ポートのサプライヤーを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し`CoCreateInstance`でポート サプライヤーの`GUID`(これはこのインターフェイスを取得する一般的な方法で) このインターフェイスを返します。 例えば:  
  
```cpp#  
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
  
 呼び出し[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)によって使用されている現在のポート サプライヤーを表す、このインターフェイスを返します[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]します。  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)ポートを作成したポートのサプライヤーを表す、このインターフェイスを返します。  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)の一覧を表します`IDebugPortSupplier`インターフェイス (、`IEnumDebugPortSuppliers`インターフェイスがから取得した[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)に登録されているすべてのポートサプライヤーを表す[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]).  
  
 デバッグ エンジンは、通常、ポート サプライヤーは操作できません。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPortSupplier2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|ポート サプライヤーの名前を取得します。|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|ポート サプライヤーの識別子を取得します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|ポート サプライヤーからポートを取得します。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|既に存在するポートを列挙します。|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|ポート サプライヤーが新しいポートの追加をサポートしていることを確認します。|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|ポートを追加します。|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|ポートを削除します。|  
  
## <a name="remarks"></a>Remarks  
 ポート サプライヤーは、名前と ID によって識別される、追加、ポートを削除し、およびポート サプライヤーを提供するすべてのポートを列挙できます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)

