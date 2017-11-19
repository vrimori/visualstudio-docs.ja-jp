---
title: "IDebugProcess3::Step |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::Step
helpviewer_keywords: IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7bd62bc141e3c5c63a887f683b7e252d466ea83
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
1 つの命令またはステートメントにステップ イン プロセスをさせます。  
  
> [!NOTE]
>  このメソッドは、の代わりに使用する必要があります[ステップ](../../../extensibility/debugger/reference/idebugprogram2-step.md)です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ステップが実行されているスレッドを表すオブジェクト。  
  
 `sk`  
 [in]1 つ、 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)値。  
  
 `step`  
 [in]1 つ、 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。エラー コードを返しますそれ以外の場合。  
  
## <a name="remarks"></a>コメント  
 任意のスレッドの同期またはスレッド間の通信が、特定のスレッドがステップ実行時プロセスの他のスレッドを実行します。  
  
 **警告**停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。 この呼び出しを処理中にそれ以外の場合、デバッガーがハングアップします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)