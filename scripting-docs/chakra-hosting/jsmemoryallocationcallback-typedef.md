---
title: JsMemoryAllocationCallback Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryallocationcallback-typedef"></a>JsMemoryAllocationCallback Typedef
メモリ割り当てイベントに対してユーザーによって実装されたコールバック ルーチン。  
  
## <a name="syntax"></a>構文  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 callbackState  
 JsSetRuntimeMemoryAllocationCallback に渡される状態。  
  
 allocationEvent  
 型割り当てイベントの種類。  
  
 allocationSize  
 割り当てのサイズ。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 JsMemoryAllocate イベントでは、true を返すことにより、ランタイムの割り当てを続行できます。 false を返すと、割り当て要求が拒否されることを示します。 戻り値は、他の割り当てイベントでは無視されます。  
  
## <a name="remarks"></a>コメント  
 このコールバックを登録するには、JsSetRuntimeMemoryAllocationCallback を使用します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)