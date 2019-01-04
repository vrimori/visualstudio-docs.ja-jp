---
title: IDebugProgramNode2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15d811cb01f7d5201f8cc1d7f64795c0197cf99c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848062"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
このインターフェイスは、デバッグ可能なプログラムを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) やカスタム ポート サプライヤーは、デバッグ可能なプログラムを表すためには、このインターフェイスを実装します。 このインターフェイスが実装する同一のオブジェクトに通常実装、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス。 このインターフェイスに登録されて[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]呼び出して[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)をこのインターフェイスを返します。 呼び出すことによってこのインターフェイスを受信カスタム ポート サプライヤー [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)します。 呼び出すことによってこのインターフェイスを受け取る、DE[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProgramNode2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|プログラムの名前を取得します。|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|プログラムをホストするプロセスの名前を取得します。|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|プログラムをホストするプロセスのシステム プロセス識別子を取得します。|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|非推奨とされます。 使用しないでください。|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|非推奨とされます。 使用しないでください。 参照してください、 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)別のアプローチのインターフェイス。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|このプログラムを実行している DE の識別子と名前を取得します。|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|非推奨とされます。 使用しないでください。|  
  
## <a name="remarks"></a>Remarks  
 セッション デバッグ マネージャー (SDM) を呼び出す通常[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)このインターフェイスを取得します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)