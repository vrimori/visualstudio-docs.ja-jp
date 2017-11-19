---
title: "IDebugProgram2::Continue |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Continue
helpviewer_keywords: IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81a8bf23ee0272f448c49b6d58d194d3ba261509
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
停止状態からこのプログラムの実行が続行されます。 (ステップ) など、以前の実行状態が保持されます、しを再度実行して、プログラムを開始します。  
  
> [!NOTE]
>  このメソッドは推奨されません。 使用して、[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、デバッグ中のプログラムの数、またはプログラムは stopping イベントの生成に関係なく、このプログラムで呼び出されます。 実装では、(ステップ) などの以前の実行状態を維持することはありませんが、以前の実行を完了する前に停止したかのように実行を続行します。 このプログラムにスレッドが、ステップ オーバー操作を行っていた動作、他のプログラムによって停止し、し、このメソッドが呼び出されたために、停止されましたには、プログラムは元のステップ オーバー操作を完了する必要があります。  
  
> [!WARNING]
>  停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。 この呼び出しを処理中にそれ以外の場合、デバッガーがハングアップします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)