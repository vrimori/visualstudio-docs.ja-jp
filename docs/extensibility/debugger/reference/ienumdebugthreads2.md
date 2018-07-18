---
title: IEnumDebugThreads2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3405a8ab52591e79f5a865016b68c69c61e6cf8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125467"
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [手順](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [実行します。](../../../extensibility/debugger/reference/idebugprocess3-execute.md)