---
title: IDebugProcess3::Continue |Microsoft Docs
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
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fe66b5cc4c07f55d821d00b8769664fb3c24445
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276641"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このプロセスを停止状態から実行が続行されます。 (ステップ) など、以前の実行状態の保持、し、もう一度実行して、プロセスを開始します。  
  
> [!NOTE]
>  このメソッドは、の代わりに使用する必要があります[続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md)します。  
  
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
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)に続くスレッドを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、デバッグ中のプロセスの数、または停止イベントを生成するプロセスに関係なく、このプロセスで呼び出されます。 実装する必要があります (ステップ) などの以前の実行状態を保持し、ことはありませんが、前の実行を完了する前に停止したように実行を続行します。 、内のスレッドの場合このプロセスをステップ オーバー操作を行っていたれ、他のプロセスが停止したために停止されましたし、`Continue`が呼び出されると、指定したスレッドは、元のステップ オーバー操作を完了する必要があります。  
  
 **警告**stopping イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md); この呼び出しを処理中にそれ以外の場合、デバッガーがハングします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

