---
title: "IDebugManagedObject::GetManagedObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugManagedObject::GetManagedObject
helpviewer_keywords: IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d73d68edcae0de9ca5834d6c622660e83cb72afa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
マネージ オブジェクトを表すインターフェイスを返します。  
  
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
 [out]マネージ オブジェクトを表すインターフェイスを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドから返されたインターフェイスを呼び出すためのメソッドを許可するマネージ クラスによって実装されるインターフェイスのクエリを実行できます。  
  
## <a name="see-also"></a>参照  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)