---
title: "IDebugProgram2::GetProcess | Microsoft Docs"
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
  - "IDebugProgram2::GetProcess"
helpviewer_keywords: 
  - "IDebugProgram2::GetProcess"
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムを実行しているプロセスを取得します。  
  
## 構文  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### パラメーター  
 `ppProcess`  
 \[出力\] プロセスを表す [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) のインターフェイスを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 デバッグ エンジン \(DE\) は [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) のインターフェイスを実装していない場合de\-DE では実装しますがプロセスを判断し実行するこのメソッドの実装を満たすことができないため `E_NOTIMPL` を常に返す必要です。  
  
 `IDebugEngineLaunch2` のインターフェイスを実装するにはプロセスの作成方法を認識しますが必要であることを意味します ; したがってde\-DE の [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) のインターフェイスの実装はプロセスを実行しているかを確認できます。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)