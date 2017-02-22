---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
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
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムが停止しても \(または拒否します\) 式の評価が特定のスレッドに発生するようにします。  
  
## 構文  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### パラメーター  
 `pOriginatingProgram`  
 \[入力\] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) に式を評価するプログラムです。  
  
 `dwTid`  
 \[出力\] スレッドの ID を指定します。  
  
 `dwEvalFlags`  
 \[入力\] 評価がどのように実行されるかを指定する [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) の列挙体のフラグの組み合わせ。  
  
 `pExprCallback`  
 \[入力\] 式の評価中に発生するイベントをデバッグするために使用する [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のオブジェクト。  
  
 `fWatch`  
 \(\)`TRUE``dwTid` で識別されるスレッドの式の評価でない場合は\[入力\]; それ以外の場合はそのスレッド `FALSE`\(\) の式の評価が拒否されます。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 デバッグ セッションのプログラム マネージャーが \(SDM\) を呼び出すと式を評価することが `pOriginatingProgram` のパラメーターではこのメソッドを呼び出してほかのアタッチしたプログラムをすべて識別される通知します。  
  
 1 個のプログラムの式の評価により `IDispatch` のプロパティの評価または関数評価が原因でコードを別ので実行される場合があります。  この理由からこのメソッドはスレッドがこのプログラムで停止するかどうかにかかわらず式の評価を実行し完了するようにします。  
  
## 参照  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)