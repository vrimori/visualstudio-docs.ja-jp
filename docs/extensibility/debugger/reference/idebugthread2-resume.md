---
title: IDebugThread2::Resume |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f51fdb05fb44a23227a1a35fd6504f2d18aa804
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
スレッドの実行を再開します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwSuspendCount`  
 [out]再開操作の後に、中断カウントを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドをデクリメントする中断カウントを呼び出して各実行が再開に実際には 0 に達すると、その時点、までです。 この中断の数が表示されます、**スレッド**デバッグ ウィンドウです。  
  
 このメソッドを呼び出すたびに、必要がありますを前回呼び出したとき、 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)メソッドです。 何回中断カウントの決定、`IDebugThread2::Suspend`メソッドがこれまで呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)