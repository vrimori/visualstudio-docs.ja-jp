---
title: IDebugCanStopEvent2::CanStop |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f32fae422d0f8b16bef91dbdd28471456648c1df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247250"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

現在のコードの場所で停止またはだけ実行を続行するかどうか (DE) デバッグ エンジンに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]0 以外の値 (`TRUE`) 現在のコードの場所に、DE を停止する場合は、0 (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 通常、このイベントの受信側を呼び出します、 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)を停止する必要がある、DE、理由を特定のメソッドに呼び出し、`IDebugCanStopEvent2::CanStop`適切な応答を持つメソッド。  
  
 を、DE が停止した場合は、停止の理由を説明するイベントを送信します。 通常は、2 つのイベントによって表されるユーザーまたは信号区切り、送信される、 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)インターフェイス、およびブレークポイント イベントによって表される、 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

