---
title: IEnumDebugBoundBreakpoints2::Reset |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugBoundBreakpoints2::Reset
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Reset
ms.assetid: 0f0522a5-6a97-4c4e-859b-cc4476e6c527
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4b5e4849c13e5a7c9e88dd2be450cb75d4be70a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928153"
---
# <a name="ienumdebugboundbreakpoints2reset"></a>IEnumDebugBoundBreakpoints2::Reset
最初の要素を列挙値をリセットします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが呼び出された後、次回の呼び出し、[次](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)メソッドが列挙体の最初の要素を返します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)