---
title: IDebugReference2::GetDerivedMostReference |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: f6e8998ca881bbeb4a90405ab01577bf6be18f33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858356"
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