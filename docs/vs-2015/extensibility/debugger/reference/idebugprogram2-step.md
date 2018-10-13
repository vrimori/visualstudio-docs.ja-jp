---
title: IDebugProgram2::Step |Microsoft Docs
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
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24946452e4ca1f595b076d61d165876c072e4537
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209678"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ステップを実行します。  
  
> [!NOTE]
>  このメソッドが非推奨とされます。 使用して、[手順](../../../extensibility/debugger/reference/idebugprocess3-step.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ステップが実行されているスレッドを表すオブジェクト。  
  
 `sk`  
 [in]値、 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)ステップの種類を指定する列挙体。  
  
 `step`  
 [in]値、 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)ステップの単位を指定します (たとえば、ステートメントまたは命令) を列挙します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 任意のスレッドの同期またはスレッド間の通信が発生したとき、プログラム内の他のスレッドは、特定のスレッドがステップ実行時に実行する必要があります。  
  
> [!WARNING]
>  停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md); この呼び出しを処理中にそれ以外の場合、デバッガーがハングします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

