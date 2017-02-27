---
title: "IDebugEngine2::RemoveSetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::RemoveSetException"
helpviewer_keywords: 
  - "IDebugEngine2::RemoveSetException"
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngine2::RemoveSetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定した例外を削除します。デバッグ エンジンによって処理されなくなります。  
  
## 構文  
  
```cpp#  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### パラメーター  
 `pException`  
 \[入力\] 例外を削除する [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) 記述する構造体。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 削除される例外は [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) のメソッドへの前の呼び出しによって設定する必要があります。  
  
 すべての例外をすぐに削除するには[RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)