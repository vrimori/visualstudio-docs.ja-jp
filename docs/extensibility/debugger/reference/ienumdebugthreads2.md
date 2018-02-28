---
title: "IEnumDebugThreads2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b03d9adbec92986ea8a1cf0f589bd451107a611f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
この interfac では、現在のデバッグ セッションで実行中のスレッドを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、プログラム内のスレッドの一覧を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)このインターフェイスを表すすべてのスレッド、プロセスで実行されているすべてのプログラムの一覧を取得します。 呼び出す[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)プログラムで実行しているスレッドのリストを表す、このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugThreads2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|指定した列挙のシーケンス内のスレッド数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|指定した列挙のシーケンス内のスレッド数をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|列挙のシーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|現在のものと同じ列挙の状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|列挙子内のスレッドの数を取得します。|  
  
## <a name="remarks"></a>コメント  
 Visual Studio が通常を更新するには、このインターフェイスを取得、**スレッド**ウィンドウでも呼び出すために、リストの最初のスレッドを取得したり[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)、[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)、および[ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md)です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [手順](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [実行します。](../../../extensibility/debugger/reference/idebugprocess3-execute.md)