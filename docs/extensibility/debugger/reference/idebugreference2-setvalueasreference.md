---
title: "IDebugReference2::SetValueAsReference |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e295ad3fd09a8b5dbaa17cdd6f10f3cb8a9ff1b9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
別の参照からの参照の値を設定します。 将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `rgpArgs`  
 [in]配列[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)オブジェクト参照値を設定する方法を決定するために使用します。  
  
 `dwArgCount`  
 [in]配列内の参照の数。  
  
 `pValue`  
 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)プロパティ値を設定する対象のオブジェクト。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位の最大時間。 使用して`INFINITE`無制限に待機します。  
  
## <a name="return-value"></a>戻り値  
 常に `E_NOTIMPL` を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
