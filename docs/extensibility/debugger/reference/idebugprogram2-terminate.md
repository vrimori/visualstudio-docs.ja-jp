---
title: "IDebugProgram2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムを終了します。  
  
## 構文  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 可能であればプログラムが終了されプロセスからアンロードされます ; はデバッグ エンジンは \(DE\)必要なクリーンアップを実行します。  
  
 このメソッドまたは [終了](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) のメソッドでデバッグを停止するのに応じて通常IDE によって呼び出されます。  このメソッドの実装では理想的なプロセス内のプログラムを終了します。  これができない場合de\-DE はプログラムでこのプロセスは実行されるのを防ぐ必要があります \(必要なクリーンアップを行うため\)。  `IDebugProcess2::Terminate` のメソッドが IDE で呼び出された場合このプロセス全体が `IDebugProgram2::Terminate` のメソッドが呼び出された後にある時点で終了します。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [終了](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)