---
title: "IDebugProgram2::GetDisassemblyStream | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
helpviewer_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムの逆アセンブリのストリームまたはこのプログラムの一部を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```c#  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### パラメーター  
 `dwScope`  
 \[入力\] コード ストリームの範囲を定義する [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) の列挙値を指定します。  
  
 `pCodeContext`  
 \[入力\] コード ストリームの開始するための位置を表す [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) のオブジェクト。  
  
 `ppDisassemblyStream`  
 \[入力\] コード ストリームを表す [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  コードがこの特定のアーキテクチャではサポートされて `E_DISASM_NOTSUPPORTED` を返します。  
  
## 解説  
 `dwScopes` のパラメーターに [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) の列挙型に設定済みの `DSS_HUGE` のフラグが設定されている場合すべてのファイルまたはモジュールの多くの構成命令は逆アセンブルは返すと想定されます。  `DSS_HUGE` フラグが設定されていない場合逆アセンブリは一つの関数の小さな領域通常どおりに制限されることになります。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)