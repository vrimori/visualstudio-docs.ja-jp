---
title: "IDebugEngineProgram2::Stop | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::Stop"
helpviewer_keywords: 
  - "IDebugEngineProgram2::Stop"
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムで実行しているすべてのスレッドを中断します。  
  
## 構文  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```c#  
int Stop();  
```  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはこのプログラムが複数のプログラミング環境でデバッグするときに呼び出されます。  ほかのプログラムからの停止のイベントを受け取るとこのメソッドはプログラムで呼び出されます。  このメソッドの実装では非同期 ; 必要があります。つまりメソッドはすべてのスレッドがこのの前に終了する必要があります。  このメソッドの実装ではことができます。このプログラムの [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) のメソッドを呼び出して簡単です。  
  
 デバッグ イベントをこのメソッドに対して送信されません。  
  
## 参照  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)