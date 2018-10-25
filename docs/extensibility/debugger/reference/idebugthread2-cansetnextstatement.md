---
title: IDebugThread2::CanSetNextStatement |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af14a59251aecf7e54d156d777db0f1d799348a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891324"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
現在の命令ポインターが特定のスタック フレームに設定することができるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStackFrame`  
 今後使用するために予約されていますnull 値に設定します。 Null 値の場合は、現在のスタック フレームを使用します。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)実行されるコードの場所を記述するオブジェクトとそのコンテキスト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが戻る場合`S_OK`、呼び出して、 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)実際には、次のステートメントを設定します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)