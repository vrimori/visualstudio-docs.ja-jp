---
title: "IDebugExceptionEvent2::CanPassToDebuggee |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef10fd3ca7f41c2afd1c827fb71ca2178782e3d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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