---
title: IDebugExceptionEvent2::CanPassToDebuggee |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ccf980fb3d5b357b6211674ca8b99132d81fae1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041010"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
デバッグ エンジン (DE) に実行が再開されるときにデバッグするプログラムにこの例外を渡すことがサポートしているかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>戻り値  
 どちらかを返します`S_OK`(例外は、プログラムに渡されることができます) または`S_FALSE`(は、例外を渡すことができません)。  
  
## <a name="remarks"></a>Remarks  
 DE、デバッグ対象に渡すのための既定のアクションが必要です。 IDE が表示される、 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)イベントと呼び出し、[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)メソッドを呼び出さずに、`CanPassToDebuggee`メソッド。 そのため、DE には、かどうか例外を渡すための既定のケースが必要です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)