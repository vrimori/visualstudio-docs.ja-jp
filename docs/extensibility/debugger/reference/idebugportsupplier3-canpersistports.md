---
title: "IDebugPortSupplier3::CanPersistPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはポートのサプライヤーがデバッガーの呼び出し \(ディスクにして記述してポート\) 保持できるかどうかを判定します。  
  
## 構文  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```c#  
int CanPersistPorts();  
```  
  
#### パラメーター  
 なし。  
  
## 戻り値  
 ポートが保持できるポートが保持できないことを示す `S_OK` または `S_FALSE`。  
  
## 解説  
 ポートのサプライヤーが保持できるポート再びインスタンスが作成されたときにこれらを再度読み込むに破棄されるとき" " を参照してください。  
  
## 参照  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)