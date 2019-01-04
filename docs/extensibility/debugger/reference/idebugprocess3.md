---
title: IDebugProcess3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 499f495308f885230bb14f34abe87c4f735ddb24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962502"
---
# <a name="idebugprocess3"></a>IDebugProcess3
このインターフェイスは、実行中のプロセスとそのプログラムを表します。 このインターフェイスは、いくつかのメソッドの代替が存在する、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス。 プロセスのすべてのプログラムに制御を提供します。  
  
> [!NOTE]
>  [引き続き](../../../extensibility/debugger/reference/idebugprogram2-continue.md)、 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)、および[手順](../../../extensibility/debugger/reference/idebugprogram2-step.md)メソッドは非推奨し、使用できなくする必要があります。 対応するメソッドを使用して、`IDebugProcess3`インターフェイスの代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、グループとしてプログラムを管理するカスタム ポートのサプライヤーによって実装されます。 プログラムのグループとして管理対象は、その実行を制御し、式エバリュエーターの言語を確立できます。 ポート サプライヤーによってこのインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、このプロセスで識別されたプログラムのグループと対話するために主にセッション デバッグ マネージャー (SDM) によって呼び出されます。  
  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)をこのインターフェイスを取得するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)、`IDebugProcess3`次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|実行や、プロセスのステップが続行されます。|  
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|プロセスの実行を開始します。|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|手順は、1 つの命令またはプロセス内のステートメントを転送します。|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|デバッグ プロセスを起動したことの理由を取得します。|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|デバッグ エンジンは、適切な式エバリュエーターを読み込めるように、ホスト言語を設定します。|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|このプロセスに設定されている言語を取得します。|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|このプロセスの編集と続行 (ENC) を無効にします。<br /><br /> カスタム ポート サプライヤーはこのメソッドを実装していません (常に返すことは`E_NOTIMPL`)。|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|このプロセスの ENC の状態を取得します。<br /><br /> カスタム ポート サプライヤーはこのメソッドを実装していません (常に返すことは`E_NOTIMPL`)。|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|使用可能なデバッグ エンジンの一意の識別子の配列を取得します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)