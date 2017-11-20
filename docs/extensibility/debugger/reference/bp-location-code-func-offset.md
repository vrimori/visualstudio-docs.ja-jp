---
title: "BP_LOCATION_CODE_FUNC_OFFSET |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords: BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ccaf1b9c4aee385f26000bb6a397f32984dfe1a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
コード内の関数内のブレークポイントのオフセットの位置をについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## <a name="members"></a>メンバー  
 `bstrContext`  
 ブレークポイントのコンテキスト、通常、呼び出し履歴に見られるようメソッドまたは関数の名前。  
  
 `pFuncPos`  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)関数の名前、および関数の先頭からの相対位置を記述するオブジェクト。  
  
## <a name="remarks"></a>コメント  
 この構造体のメンバーである、 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)構造体、共用体の一部として。  
  
 `pFuncPos`メンバーは関数のブレークポイントを設定する場所を示します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)