---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

使用されていません。  使用しないでください。  
  
## 構文  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### パラメーター  
 `pMDMProgram`  
 \[入力\] プログラムをアタッチするに [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 表すインターフェイス。  
  
 `pCallback`  
 \[入力\] SDM にデバッグ イベントを送信するために使用する [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のインターフェイス。  
  
 `dwReason`  
 \[入力\] アタッチする理由を指定する [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) の列挙体の値。  
  
## 戻り値  
 実装は `E_NOTIMPL` を常に返す必要です。  
  
## 解説  
  
> [!WARNING]
>  [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] 時点ではこのメソッドは使用されなくなり`E_NOTIMPL` を常に返す必要です。  別の方法の [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) のインターフェイスはプログラムのノードに示す必要がある場合はアタッチできないまたはプログラムのノードがプログラム `GUID` を設定する " " を参照してください。  それ以外 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドを実装します。  
  
## Visual Studio 2005 以前  
 このメソッドはをデバッグするプログラムのアドレス空間にします runs 実装する必要があります。  それ以外の場合は `S_FALSE` を返す必要があります。  
  
 このメソッドが呼び出されるとde\-DE は [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) インターフェイスのこのインスタンスに対して既に送られなかったら[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) と [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) のイベント オブジェクトはイベント送信 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) のオブジェクト。  [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) のイベント オブジェクトは`dwReason` のパラメーターがの場合 `ATTACH_REASON_LAUNCH` 送信されます。  
  
 DE は [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) のイベント オブジェクトによって提供される [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) のオブジェクトの [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) のメソッドを呼び出して de\-DE によって実装される `IDebugProgram2` のオブジェクトのインスタンス データにするプログラムの GUID 保存する必要があります。  
  
## 参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)