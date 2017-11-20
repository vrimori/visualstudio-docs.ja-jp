---
title: "BP_LOCATION_CODE_ADDRESS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_ADDRESS
helpviewer_keywords: BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0dc53f11dd4ba06488dbd53b9a1f4014268412d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
コード内のアドレスのブレークポイントの場所について説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## <a name="members"></a>メンバー  
 `bstrContext`  
 ブレークポイントのコンテキスト、通常、呼び出し履歴に見られるようメソッドまたは関数の名前。  
  
 `bstrModuleUrl`  
 ブレークポイントを含むモジュールの URL です。  
  
 `bstrFunction`  
 ブレークポイントを含む関数の名前。  
  
 `bstrAddress`  
 バインドする式エバリュエーターで解析するブレークポイントのアドレス、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)オブジェクト。  
  
## <a name="remarks"></a>コメント  
 この構造体のメンバーである、 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)構造体、共用体の一部として。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)