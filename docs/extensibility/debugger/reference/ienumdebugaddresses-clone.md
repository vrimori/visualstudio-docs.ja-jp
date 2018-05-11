---
title: IEnumDebugAddresses::Clone |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b6b5ddb4eabcbc3d15650e91ee7cecd7fdbb648
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
このメソッドは、個別のオブジェクトとして現在の列挙型のコピーを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugAddresses ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]個別のオブジェクトとしてこの列挙体のコピーを返します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 列挙体のコピーでは、このメソッドが呼び出されたときに元と同じ状態がします。 ただし、コピーのと、元の状態は別に、個別に変更することができます。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)