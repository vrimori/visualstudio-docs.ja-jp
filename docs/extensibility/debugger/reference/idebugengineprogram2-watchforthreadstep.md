---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

実行を監視実行または停止 \(の場合\)特定のスレッドの発生に表示されます。  
  
## 構文  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### パラメーター  
 `pOriginatingProgram`  
 \[入力\] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) にステップ実行できます。  
  
 `dwTid`  
 \[出力\] スレッドの ID を確認するように指定します。  
  
 `fWatch`  
 \[入力\]`TRUE`\(\) 以外の方法は `dwTid` によって識別されるスレッドの監視を開始します ; それ以外の `FALSE`\(\) はメジャーは `dwTid` の実行を監視できますが停止します。  
  
 `dwFrame`  
 \[入力\] ステップの種類を制御するフレームのインデックスを指定します。  これは値であるゼロ \(0\)ステップの種類「ステップに」である場合プログラムは `dwTid` によって識別されるスレッドが実行されるたびに停止します。  `dwFrame` がゼロ以外の場合ステップの種類については「」`dwTid` によって識別されるスレッドがインデックスが等しくないか`dwFrame` 高いによってスタック フレームで実行している場合にのみプログラムが停止します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 デバッグ セッションのステップ マネージャーでこの \(SDM\) メソッドを呼び出すと `pOriginatingProgram` のパラメーターで識別される他のプログラムにアタッチしたプログラムをすべて通知されます。  
  
 このメソッドは同じスレッドの手順でのみ有効です。  
  
## 参照  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)