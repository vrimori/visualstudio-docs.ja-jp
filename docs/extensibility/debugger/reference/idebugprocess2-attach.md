---
title: "IDebugProcess2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスにセッションの \(SDM\) デバッグ マネージャーをアタッチします。  
  
## 構文  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### パラメーター  
 `pCallback`  
 \[入力\] デバッグ イベント通知のために使用される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のオブジェクト。  
  
 `rgguidSpecificEngines`  
 \[出力\] プロセスで実行するプログラム デバッグに使用するデバッグ エンジンの GUID の配列。  このパラメーターは null になることがあります。  詳細については" 解説 " を参照してください。  
  
 `celtSpecificEngines`  
 \[入力\] `rghrEngineAttach` の配列の `rgguidSpecificEngines` の配列とサイズのデバッグ エンジンの数。  
  
 `rghrEngineAttach`  
 \[入力出力\] HRESULT コードの配列はデバッグ エンジンによって返される。  配列のサイズは `celtSpecificEngines` のパラメーターで指定されます。  各コードは`S_OK` または `S_ATTACH_DEFERRED` です。  後者は機能しますがプログラムに現在割り当てられていないことを示します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表は他の値を示します。  
  
|値|Description|  
|-------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定されたプロセスがデバッガーに既にアタッチされます。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|セキュリティ違反が前の手順の間に発生しました。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|デスクトップ プロセスにデバッガーをアタッチすることはできません。|  
  
## 解説  
 プロセスへのアタッチを `rgguidSpecificEngines` の配列で指定したデバッグ エンジン \(DE\) がデバッグできるそのプロセスを実行するすべてのプログラムで SDM をアタッチします。  `rgguidSpecificEngines` のパラメーターを null 値に設定するかまたは配列にプロセスのすべてのプログラムにアタッチするに `GUID_NULL` を追加します。  
  
 プロセスに発生するすべてのデバッグ イベントは[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) の特定のオブジェクトに送信されます。  `IDebugEventCallback2`このオブジェクトは SDM がこのメソッドを呼び出すと提供されます。  
  
## 参照  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)