---
title: "IEnumDebugCodeContexts2::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::GetCount"
ms.assetid: 74c52fcf-688c-40df-9acd-29b3b84e6216
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugCodeContexts2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列挙体の要素数を返します。  
  
## 構文  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### パラメーター  
 `pcelt`  
 \[入力\] 列挙体の要素数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは `Next``Clone``Skip` と `Reset` のメソッドに実行する必要があることを指定する通常の COM 列挙インターフェイスの一部ではありません。  
  
## 参照  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)