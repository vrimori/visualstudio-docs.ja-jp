---
title: "複数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "複数の列挙型"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 複数
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

イベント属性を指定します。  
  
## 構文  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## メンバー  
 EVENT\_ASYNCHRONOUS  
 イベントは非同期なイベントへの応答が必要なことを示します。  
  
 EVENT\_SYNCHRONOUS  
 イベントが同期されていることを示しています ; [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) して応答。  
  
 EVENT\_STOPPING  
 これが停止のイベントであることを示します。  `EVENT_ASYNCHRONOUS` または `EVENT_SYNCHRONOUS` と組み合わせる必要があります。  
  
 EVENT\_ASYNC\_STOP  
 非同期停止のイベントが表示されます。  現在このようなイベントはありません。  このフラグはのプレースホルダーです。  
  
 EVENT\_SYNC\_STOP  
 同期停止のイベント \(`EVENT_SYNCHRONOUS` と `EVENT_STOPPING` の組み合わせ\) を示します。  この値はデバッグ エンジン \(DE\) によって停止イベントを送信するときに使用されます。  [実行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)[ステップ](../../../extensibility/debugger/reference/idebugprogram2-step.md)または [続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md) への応答が呼び出しによって行われます。  
  
 EVENT\_IMMEDIATE  
 IDE に迅速かつ同期的に送信されるイベントを示します。  このフラグは `EVENT_ASYNCHRONOUS``EVENT_SYNCHRONOUS`または `EVENT_SYNC_STOP` などの他のフラグによって応答の機能 \(存在する場合\) がわかっているということおよびイベントの種類を示すようになります。  
  
 EVENT\_EXPRESSION\_EVALUATION  
 イベントは式の評価結果があります。  
  
## 解説  
 これらの値は [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) のメソッドの `dwAttrib` のパラメーターに渡されます。  
  
 これらの値はビットごとの `OR` と組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)