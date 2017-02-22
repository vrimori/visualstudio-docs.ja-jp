---
title: "IDebugProcess2::CanDetach | Microsoft Docs"
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
  - "IDebugProcess2::CanDetach"
helpviewer_keywords: 
  - "IDebugProcess2::CanDetach"
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ セッションの管理にプロセスをデタッチ \(SDM\) できるかどうかを判断します。  
  
## 構文  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## 戻り値  
 成功するとデバッガーがプロセスからデタッチできない場合は `S_OK.` は `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [CanDetach](../Topic/IDebugProgram2::CanDetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)