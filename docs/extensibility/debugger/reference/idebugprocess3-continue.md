---
title: "IDebugProcess3::Continue |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c112a29d6b936b53aef5be5366f4066a66265e4f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
このプロセスを停止状態から実行が続行されます。 (ステップ) など、以前の実行状態が保持されます、しを再度実行して、プロセスを開始します。  
  
> [!NOTE]
>  このメソッドは、の代わりに使用する必要があります[続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md)です。  
  
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
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)を継続するスレッドを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、デバッグ中のプロセスの数、またはどのプロセスが停止イベントを生成に関係なく、このプロセスで呼び出されます。 実装では、(ステップ) などの以前の実行状態を維持することはありませんが、以前の実行を完了する前に停止したかのように実行を続行します。 場合内のスレッドでこのプロセスが、ステップ オーバー操作を行っていた動作と他のプロセスが停止しているために停止しましたし、`Continue`呼び出されましたが、指定されたスレッドは、元のステップ オーバー操作を完了する必要があります。  
  
 **警告**停止イベントまたは直接 (同期) イベントを送信しない[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。 この呼び出しを処理中にそれ以外の場合、デバッガーがハングアップします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
