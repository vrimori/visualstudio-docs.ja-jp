---
title: IDebugExceptionEvent2::GetException |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fad5aca8dcb548718c6acabb5c58e8c31592558
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950804"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
このイベントを発生させた例外の詳細な説明を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pExceptionInfo`  
 [入力、出力][EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)構造を例外の説明が入力されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 [C++ のみ]呼び出し元が内の任意の文字列を解放する、 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)の解放と構造体、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)構造内のオブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)