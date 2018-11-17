---
title: IDebugProgramNode2 |Microsoft Docs
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
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e0014b1b60ee01d693adc43e6dff54cf17cdf46
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747485"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、デバッグ可能なプログラムを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) やカスタム ポート サプライヤーは、デバッグ可能なプログラムを表すためには、このインターフェイスを実装します。 このインターフェイスが実装する同一のオブジェクトに通常実装、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス。 このインターフェイスに登録されて[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]呼び出して[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)します。  
  
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
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)

