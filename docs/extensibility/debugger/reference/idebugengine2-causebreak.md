---
title: IDebugEngine2::CauseBreak |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a27d0dd5c501076f7ee2354736b989a441395df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954957"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
すべてのプログラムによってこのデバッグ エンジン (DE)、次回の実行を停止するデバッグ中の要求を実行すると、スレッドの 1 つ試行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは非同期: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)次に、プログラムはこのメソッドが呼び出された後に実行しようとしたときにイベントが送信されます。  
  
## <a name="see-also"></a>関連項目  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)