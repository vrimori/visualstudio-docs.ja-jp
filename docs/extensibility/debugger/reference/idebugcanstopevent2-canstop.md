---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
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
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンを現在の \(DE\) コード位置で停止するか処理を続行するかどうかを通知します。  
  
## 構文  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### パラメーター  
 `fCanStop`  
 \[入力\] しますが現在のコード位置で停止した場合は `TRUE`\(\); それ以外の `FALSE`\(\)。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このイベントのハンドラーはde\-DE が停止する原因を判断するに [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md) のメソッドを呼び出して適切な応答 `IDebugCanStopEvent2::CanStop` のメソッドを呼び出します。  
  
 DE stops の実行が停止の理由を説明するイベントを送信します。  送信2 種類のイベント[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) のインターフェイスで表されるユーザーまたはときに中断と [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) のインターフェイスで表されるブレークポイント イベントがあります。  
  
## 参照  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)