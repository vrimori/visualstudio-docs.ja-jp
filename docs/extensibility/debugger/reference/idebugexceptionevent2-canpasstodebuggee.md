---
title: IDebugExceptionEvent2::CanPassToDebuggee |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0ffea7be736cbf6d04c368ba6124d0faf22be61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
デバッグ エンジン (DE) が実行を再開したときにデバッグするプログラムにこの例外を渡すことのオプションをサポートしているかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>戻り値  
 どちらかを返します`S_OK`(例外は、プログラムに渡すことができます) または`S_FALSE`(は、例外を渡すことができません)。  
  
## <a name="remarks"></a>コメント  
 DE、デバッグ対象に渡すのための既定のアクションが必要です。 IDE が表示される、 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)イベントと呼び出し、[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)メソッドを呼び出さず、`CanPassToDebuggee`メソッドです。 そのため、デには、か例外を渡すための既定のケースがあります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)