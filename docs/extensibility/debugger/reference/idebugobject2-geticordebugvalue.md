---
title: IDebugObject2::GetICorDebugValue |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 82315e1b2170f38cae296e2a9131f4b235add26b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114496"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
マネージ コードを表すオブジェクトをこのオブジェクトに関連付けられている値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppUnk`  
 [out]`IUnknown`このエイリアスを表すインターフェイスです。 このインターフェイスを照会することができます、`ICorDebugValue`インターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 `ICorDebugValue`オブジェクトは、値を表す共通言語ランタイム インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)