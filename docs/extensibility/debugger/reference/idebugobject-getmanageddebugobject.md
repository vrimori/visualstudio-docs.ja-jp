---
title: "IDebugObject::GetManagedDebugObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c3b0720aa8757564d06a29de2c51e53b6bb12a1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。 E_FAIL が返された場合は、この[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)マネージ値クラスのインスタンスを表していません。  
  
## <a name="remarks"></a>コメント  
 これは、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクトがなど、マネージ値クラスのインスタンスを表す必要があります、`System.Decimal`インスタンス。 ローカルのコピー、呼び出し元のオーバーヘッドによって[評価](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)が排除されます。  
  
## <a name="see-also"></a>参照  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)