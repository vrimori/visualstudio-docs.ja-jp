---
title: IDebugManagedObject::GetManagedObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f30c76dfd0c2f9dafa4844f815ce2506e70346f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917935"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
管理対象のオブジェクトを表すインターフェイスを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppManagedObject`  
 [out]管理対象のオブジェクトを表すインターフェイスを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドから返されるインターフェイスは、そのメソッドを呼び出せるように、マネージ クラスによって実装されるインターフェイスの照会できます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)