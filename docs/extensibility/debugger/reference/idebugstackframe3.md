---
title: "IDebugStackFrame3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "IDebugStackFrame3 インターフェイス"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは傍受した例外を処理する [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) を拡張します。  
  
## 構文  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは実装 \(DE\) をサポートする必要 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) インターフェイスの例外を傍受したものと同じオブジェクトこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得 `IDebugStackFrame2` のインターフェイスでは [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable の順序でメソッド  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) から継承されたメソッドに加えて `IDebugStackFrame3` は次にメソッドを公開します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|各レギュラー例外処理の前に現在のスタック フレームの例外を処理します。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|スタックが発生した場合アンワインド コードはコンテキストを返します。|  
  
## 解説  
 傍受された例外は通常の例外処理ルーチンがランタイムで呼び出される前にデバッガーが例外を処理できることを意味します。  実行時に傍受の例外の基本的な手段がない場合でも例外ハンドラーのふりあることを示します。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) は成功したすべての例外コールバック イベント中に例外が最後のコールバック内で受け取る場合\) が呼び出されます \(ただし唯一の例外は混在モード \(マネージ コードとアンマネージ コード デバッグ\) です。  DE が `IDebugStackFrame3`またはします returns を実行する IDebugStackFrame3 のエラー ::`InterceptCurrentException` \(`E_NOTIMPL` など\)デバッガーは例外を処理します。  
  
 例外の傍受してユーザーがデバッグ対象の状態に対する変更を加え例外がスローされた時点で実行を再開できるようにすることができます。  
  
> [!NOTE]
>  傍受された例外は共通言語ランタイムで実行するプログラムのマネージ コードでのみ使用できます \(CLR\)。  
  
 デバッグ エンジンは`SetMetric` の関数のことを使用して実行時に値 1 に 「」 metricExceptions を設定することによって傍受の例外をサポートすることを示します。  詳細については、「[デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)」を参照してください。  
  
## 必要条件  
 ヘッダー: msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)