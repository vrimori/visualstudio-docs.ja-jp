---
title: IDebugReference2::GetDerivedMostReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: da924444d30d0cb3022601d1ed6931ef605fa888
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892927"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
参照の最派生参照を取得します。 将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppDerivedMost`  
 [out]返します、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)最派生プロパティを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 常に `E_NOTIMPL` を返します。  
  
## <a name="remarks"></a>Remarks  
 たとえば、このプロパティを実装するオブジェクトを記述する`ClassRoot`がのインスタンス化では実際には、`ClassDerived`から派生する`ClassRoot`、このメソッドから返されます、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)オブジェクト参照を表す、`ClassDerived`オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)