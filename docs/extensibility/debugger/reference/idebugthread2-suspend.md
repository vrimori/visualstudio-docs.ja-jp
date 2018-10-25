---
title: IDebugThread2::Suspend |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9da385dc9f50ec66b45df1c9955f338a6c550467
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905403"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
スレッドを中断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwSuspendCount`  
 [out]中断操作の後に、中断カウントを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを呼び出すたびには、0 より大きい中断カウントがインクリメントします。 この中断の数が表示されます、**スレッド**デバッグ ウィンドウ。  
  
 このメソッドを呼び出すたびに、必要がありますそれ以降の呼び出し、[再開](../../../extensibility/debugger/reference/idebugthread2-resume.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)