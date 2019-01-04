---
title: IEnumDebugProcesses2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9b1beb5d6500b533ad713164b7cb4bec7097b255
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955920"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
このインターフェイスは、デバッグ ポートで実行中のプロセスを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート サプライヤーは、ポートで実行されているプロセスの一覧を提供するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 Visual Studio 呼び出し[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugProcesses2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|指定された数の列挙体シーケンス内のプロセスを取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|指定された数の列挙体シーケンス内のプロセスをスキップします。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|列挙子では、プロセスの数を取得します。|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio では、このインターフェイスを使用して、事前設定、**プロセス**ウィンドウ。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)