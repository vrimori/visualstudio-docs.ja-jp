---
title: IDebugStackFrame3::GetUnwindCodeContext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad47eb92af6c9ad37bafe293e6c7392613718c30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846448"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
コードのコンテキストの位置を表す場合は、スタックのアンワインド操作が発生したを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppCodeContext`  
 [out]返します、 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)スタック アンワインドが発生した場合は、コード コンテキストの位置を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合でも、このメソッドは、スタック アンワインドの後の場所のコードのコンテキストを返す可能性のあるは必ずしもスタック アンワインドが現在のスタック フレームで実際に発生することができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)