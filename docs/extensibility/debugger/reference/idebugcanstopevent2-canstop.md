---
title: IDebugCanStopEvent2::CanStop |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3e2507ba86e00434c12a67ba70cad51fa5850ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
現在のコードの場所で停止または同様の実行を続行するかどうか (DE) のデバッグ エンジンに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fCanStop`  
 [in]0 以外の値 (`TRUE`)、DE を中断するコードの現在の場所で; にある場合は 0 それ以外の場合 (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 通常、このイベントの受信側を呼び出します、 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)デが停止する理由を判断するメソッドを呼び出し、続いて、`IDebugCanStopEvent2::CanStop`適切な応答を持つメソッドです。  
  
 デを停止する場合は、停止の理由を説明するイベントを送信します。 送信、によって表されるユーザーか、信号が中断される 2 つのイベントには通常、 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)インターフェイス、およびによって表されるブレークポイント イベント、 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)