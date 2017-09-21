---
title: "IDebugProcess2::EnumThreads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::EnumThreads"
helpviewer_keywords: 
  - "IDebugProcess2::EnumThreads"
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスで実行しているすべてのスレッドのリストを取得します。  
  
## 構文  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```c#  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[入力\] プロセス内のすべてのプログラムのスレッド一覧を含む [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは各プログラムで実行中のスレッドを列挙しスレッドのプロセス ビューにまとめます。  シングル スレッドは複数のプログラムで実行される場合があります。; このメソッドは一度だけそのスレッドを列挙します。  
  
 このメソッドは重複のないプロセスのスレッド一覧を示します。  は特定のプログラムで実行中のスレッドを列挙するに [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) のメソッドを使用します。  
  
## 参照  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)