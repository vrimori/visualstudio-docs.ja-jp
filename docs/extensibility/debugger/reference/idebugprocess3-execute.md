---
title: IDebugProcess3::Execute |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 349f792826bcfaa6ec3af1e10069e9c7182868bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
このプロセスを停止状態から実行が続行されます。 (ステップ) など、以前の実行状態をクリアしを再度実行してプロセスを起動します。  
  
> [!NOTE]
>  このメソッドは、の代わりに使用する必要があります[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)スレッドの実行を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ユーザーは、他のプロセスのスレッドを停止状態から実行を起動するときに、このプロセスでこのメソッドが呼び出されます。 ユーザーを選択すると、このメソッドが呼び出されますも、**開始**コマンドを**デバッグ**IDE のメニュー。 このメソッドの実装を呼び出すなどの単純な可能性があります、[再開](../../../extensibility/debugger/reference/idebugthread2-resume.md)プロセスの現在のスレッドでのメソッドです。  
  
> [!WARNING]
>  停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。 この呼び出しを処理中にそれ以外の場合、デバッガーがハングアップします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [再開します。](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)