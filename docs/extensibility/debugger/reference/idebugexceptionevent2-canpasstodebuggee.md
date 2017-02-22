---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
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
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

実行を再開するとデバッグの \(DE\) デバッグ対象のプログラムにこの例外を渡す際のオプション エンジンをサポートするかどうかを指定します。  
  
## 構文  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## 戻り値  
 `S_OK` \(例外はプログラムに渡すことができます\) または `S_FALSE` を返します。例外はできません。  
  
## 解説  
 DEデバッグ対象に渡すことの既定のアクションが必要です。  IDE で [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) イベントを受け取り`CanPassToDebuggee` のメソッドを呼び出さないで [続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md) メソッドを呼び出すことがあります。  したがってde\-DE は例外を渡す場合も既定のケースを持つ必要があります。  
  
## 参照  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md)