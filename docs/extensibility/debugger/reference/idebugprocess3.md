---
title: "IDebugProcess3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
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
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 6b98394c4880ce78eb8069534b009ea351608cd6
ms.lasthandoff: 04/05/2017

---
# <a name="idebugprocess3"></a>IDebugProcess3
このインターフェイスは、実行中のプロセスとそのプログラムを表します。 このインターフェイスがいくつかのメソッドを代わりに存在する、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスです。 プロセス内のすべてのプログラムに制御を提供します。  
  
> [!NOTE]
>  [続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md)、 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)、および[ステップ](../../../extensibility/debugger/reference/idebugprogram2-step.md)メソッドは非推奨し、使用する必要があります。 対応するメソッドを使用して、`IDebugProcess3`インターフェイスの代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、グループとしてプログラムを管理するカスタム ポート業者によって実装されます。 プログラムは、グループとして管理されている、ときにそれらの実行を制御し、式エバリュエーターの言語を設定できます。 ポート業者によっては、このインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、このプロセスで識別されたプログラムのグループと対話するために、主にセッション デバッグ マネージャー (SDM) によって呼び出されます。  
  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)、`IDebugProcess3`次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|実行、またはプロセスをステップ実行を続行します。|  
|[実行します。](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|プロセスの実行を開始します。|  
|[手順](../../../extensibility/debugger/reference/idebugprocess3-step.md)|手順は、1 つの命令またはプロセス内のステートメントを転送します。|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|デバッグ プロセスを起動したことの理由を取得します。|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|デバッグ エンジンは、適切な式エバリュエーターを読み込むことができます、ホスト言語を設定します。|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|このプロセスに設定されている言語を取得します。|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|このプロセスの編集と続行 (ENC) を無効にします。<br /><br /> カスタム ポートのサプライヤーは、このメソッドを実装しない (常に返すか`E_NOTIMPL`)。|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|このプロセスの ENC の状態を取得します。<br /><br /> カスタム ポートのサプライヤーは、このメソッドを実装しない (常に返すか`E_NOTIMPL`)。|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|使用可能なデバッグ エンジンの一意の識別子の配列を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
