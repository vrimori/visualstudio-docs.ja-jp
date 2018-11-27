---
title: IDebugProcess3::Step |Microsoft Docs
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
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e937385fc064d9753736c87031111c654981fe8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781635"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

1 つの命令またはステートメントにステップ イン プロセスをさせます。  
  
> [!NOTE]
>  このメソッドは、の代わりに使用する必要があります[手順](../../../extensibility/debugger/reference/idebugprogram2-step.md)します。  
  
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
  
## <a name="remarks"></a>Remarks  
 任意のスレッドの同期またはスレッド間の通信が発生したとき、プロセス内の他のスレッドは、特定のスレッドがステップ実行時に実行する必要があります。  
  
 **警告**stopping イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md); この呼び出しを処理中にそれ以外の場合、デバッガーがハングします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

