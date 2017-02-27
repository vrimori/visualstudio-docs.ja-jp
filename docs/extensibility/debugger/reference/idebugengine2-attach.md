---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラム \(DE\) のデバッグ エンジンをアタッチします。  DE が SDM に実行して INPROC の場合セッションのデバッグ マネージャー \(SDM\) によって呼び出されます。  
  
## 構文  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### パラメーター  
 `pProgram`  
 \[入力\] アタッチするプログラムを表すこと [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) のオブジェクトの配列。  これらはポートのプログラムです。  
  
 `rgpProgramNodes`  
 \[入力\] プログラムのノードを表す [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) のオブジェクトの配列。各プログラムの場合は 1。  この配列のプログラムのノードは `pProgram` のと同じプログラムを表します。  プログラムのノードは de\-DE をアタッチするプログラムを指定できるようになります。  
  
 `celtPrograms`  
 \[入力\] `pProgram` と `rgpProgramNodes` の配列のプログラムまたはプログラムのノードの数。  
  
 `pCallback`  
 \[入力\] SDM にデバッグ イベントを送信するために使用する [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のオブジェクト。  
  
 `dwReason`  
 \[入力\] 次のプログラムを適用する理由を指定する [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) の列挙体の値。  詳細については、「解説」を参照してください。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 次のようにプログラムにアタッチするには3 とおりの理由があります :  
  
-   `ATTACH_REASON_LAUNCH` はユーザーがデータを含むプロセスを開始しますがプログラムにアタッチしていることを示します。  
  
-   `ATTACH_REASON_USER` はユーザーが要求したプログラム明示的に対して行われることを示します \(またはプログラムを含む\) プロセスにアタッチする機能します。  
  
-   `ATTACH_REASON_AUTO` は特定のプロセスのほかのプログラムをデバッグしますが特定のプログラムにアタッチしていることを示します。  これは自動アタッチと呼ばれます。  
  
 このメソッドが呼び出されるとde\-DE はこれらのイベントを順番に送信する必要があります :  
  
1.  \(デバッグ エンジンの特定のインスタンスに既に送られなかったら\)[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 またアタッチの理由が `ATTACH_REASON_LAUNCH` 場合はde\-DE [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) のイベントを送信する必要があります。  
  
 DE をデバッグ中のプログラムに対応するオブジェクトを取得 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) のすべてのプライベート インターフェイスを照会できます。  
  
 `pProgram` または `rgpProgramNodes` によって偽装は指定された呼び出す前に配列のプログラムのノードのメソッドを必要に応じてプログラムのノードを表す `IDebugProgram2` のインターフェイスで有効になります。  しかしこの手順は必要ではありません。  詳細については、「[セキュリティ上の問題](../../../extensibility/debugger/security-issues.md)」を参照してください。  
  
## 参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)