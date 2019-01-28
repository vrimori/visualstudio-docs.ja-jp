---
title: IDebugObject2::IsEncOutdated |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5facc3b8efed46817e99624e6b019d1498ec622
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016136"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
このメソッドは、このオブジェクトのまたは親コンテナーのエディット コンティニュの状態が古くなっているかどうかを判断します。 カスタム式エバリュエーターでは、このメソッドを常に返しますは実装しません`E_NOTIMPL`します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pfEncOutdated`  
 [out]0 以外の場合 (`TRUE`) エディット コンティニュの状態が最新でない場合は、0 (`FALSE`) でない場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  カスタム式エバリュエーターを常に返します`E_NOTIMPL`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)