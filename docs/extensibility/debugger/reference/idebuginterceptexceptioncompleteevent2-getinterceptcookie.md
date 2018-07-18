---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd7ea8d7ed7da47c88b0c2816e0cf03e7833e8f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111207"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
傍受した例外の処理が完了したときに呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pqwCookie`  
 [out]インターセプトされた例外に関連付けられている一意の値です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`; エラー コードを返しますそれ以外の場合。  
  
## <a name="remarks"></a>コメント  
 後に、 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)メソッドには、傍受した例外の処理が完了したら、送信、 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)イベント。 ハンドラーが使用できる、`GetInterceptCookie`例外に関連付けられている一意の値を取得する方法 (に渡されたのと同じ値、`InterceptCurrentException`メソッド)。  
  
## <a name="see-also"></a>関連項目  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)