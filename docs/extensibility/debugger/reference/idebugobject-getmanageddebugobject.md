---
title: IDebugObject::GetManagedDebugObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1c0b636c88c2c2e23efcc01b01eec1e421317e0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831101"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
デバッグ エンジンのアドレス空間には、管理対象のオブジェクトのコピーを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppObject`  
 [out]返します、 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)新しく作成されたマネージ オブジェクトを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。 E_FAIL が返された場合は、この[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)マネージ値クラスのインスタンスは表しません。  
  
## <a name="remarks"></a>Remarks  
 これは、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクトなどで、管理対象の値クラスのインスタンスを表す必要があります、`System.Decimal`インスタンス。 呼び出し元のオーバーヘッドがローカル コピーをすることで[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)がなくなります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)