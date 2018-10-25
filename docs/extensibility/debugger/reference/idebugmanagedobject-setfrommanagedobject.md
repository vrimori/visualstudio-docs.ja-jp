---
title: IDebugManagedObject::SetFromManagedObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: afe3431e282a8cd48ea33851cef00fba116e389a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833942"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
パラメーターとして指定された値クラスのインスタンスから値クラスのオブジェクトのインスタンスの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pManagedObject`  
 [in]新しい値を格納しているマネージ オブジェクトを表すインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドの使用によって表されるマネージ オブジェクトの変更を[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)