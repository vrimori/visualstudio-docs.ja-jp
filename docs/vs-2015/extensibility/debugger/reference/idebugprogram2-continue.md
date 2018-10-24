---
title: IDebugProgram2::Continue |Microsoft Docs
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
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d787e06c2586a2d5c3b6c48817262c80e14183d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825338"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

停止状態からこのプログラムの実行が続行されます。 (ステップ) など、以前の実行状態の保持、され、プログラムでは、もう一度実行が開始されます。  
  
> [!NOTE]
>  このメソッドが非推奨とされます。 使用して、[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)スレッドを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、デバッグ中のプログラムの数、またはプログラムは stopping イベントの生成に関係なく、このプログラムで呼び出されます。 実装する必要があります (ステップ) などの以前の実行状態を保持し、ことはありませんが、前の実行を完了する前に停止したように実行を続行します。 つまり、このプログラムでは、スレッドがステップ オーバー操作を行っていたため、他のプログラムが停止し、このメソッドが呼び出された後に停止された場合に、プログラムは元のステップ オーバー操作を完了する必要があります。  
  
> [!WARNING]
>  停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md); この呼び出しを処理中にそれ以外の場合、デバッガーがハングします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

