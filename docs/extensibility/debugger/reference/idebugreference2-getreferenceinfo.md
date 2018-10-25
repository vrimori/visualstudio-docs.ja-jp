---
title: IDebugReference2::GetReferenceInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8833b27d70a92091f809605edc81cd82a8a65f06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870004"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
取得、 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)の参照を記述する構造体。 将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFields`  
 [in]フラグの組み合わせ、 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)入力するフィールドを決定する列挙体、 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造体。  
  
 `nRadix`  
 [in]任意の数値情報を書式設定で使用する基数。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位で最大時間。 使用`INFINITE`を無期限に待機します。  
  
 `rgpArgs`  
 [in]配列の[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)オブジェクト。 今後使用するために予約されていますnull 値に設定します。  
  
 `dwArgCount`  
 [in]参照引数の数、`rgpArgs`配列。 今後使用するために予約されています0 に設定します。  
  
 `pReferenceInfo`  
 [out]A [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造、プロパティの説明が入力されます。  
  
## <a name="return-value"></a>戻り値  
 常に `E_NOTIMPL` を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)