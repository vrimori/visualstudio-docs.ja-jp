---
title: "IDebugProgram2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Attach"
helpviewer_keywords: 
  - "IDebugProgram2::Attach"
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムへのアタッチされます。  
  
## 構文  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### パラメーター  
 `pCallback`  
 \[入力\] デバッグ イベント通知に使用する [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のオブジェクト。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表は考えられるエラー コードです。  
  
|値|Description|  
|-------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定されたプログラムはデバッガーに既にアタッチされます。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|セキュリティ違反が前の手順の間に発生しました。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|デスクトップのプログラムをデバッガーにアタッチすることはできません。|  
  
## 解説  
 デバッグ エンジンはプログラム \(DE\) にアタッチするにはこのメソッドを呼び出していません。  プログラムのアドレス空間に runs しますが[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) のメソッドが呼び出されます。  デバッグ セッションのマネージャーのアドレス空間に runs します \(SDM\) が[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) のメソッドが呼び出されます。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)