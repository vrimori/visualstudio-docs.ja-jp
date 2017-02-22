---
title: "IDebugProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2"
helpviewer_keywords: 
  - "IDebugProgramNode2 インターフェイス"
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグするプログラムを表します。  
  
## 構文  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジン \(DE\) またはカスタム ポートの業者はデバッグするプログラムを表すためこのインターフェイスを実装します。  このインターフェイスは同じオブジェクトでは通常を実装する [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) のインターフェイス実装されます。  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] のこのインターフェイスは [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) を呼び出して登録されます。  
  
## 呼び出し元のメモ  
 このインターフェイスを返す呼び出し [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)。  カスタム ポートの業者は [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) を呼び出すことによってこのインターフェイスを受け取ります。  DE は [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) を呼び出すことによってこのインターフェイスを受け取ります。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProgramNode2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|プログラムの名前を取得します。|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|プロセスホスティングの名前にプログラムを取得します。|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|プロセスホスティングのシステム プロセス識別子にプログラムを取得します。|  
|[GetHostMachineName\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|使用されていません。  使用しないでください。|  
|[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|使用されていません。  使用しないでください。  別の方法については [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) のインターフェイスを参照してください。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|このプログラムを実行する DE の名前と ID を取得します。|  
|[DetachDebugger\_V7](../Topic/IDebugProgramNode2::DetachDebugger_V7.md)|使用されていません。  使用しないでください。|  
  
## 解説  
 デバッグ セッションのマネージャーは \(SDM\)このインターフェイスを取得するに [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) を呼び出します。  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)