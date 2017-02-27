---
title: "IDebugTypeFieldBuilder::CreatePointerToType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreatePointerToType"
  - "IDebugTypeFieldBuilder::CreatePointerToType"
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugTypeFieldBuilder::CreatePointerToType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定した型へのポインターを作成します。  
  
## 構文  
  
```cpp#  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```c#  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### パラメーター  
 `pTypeField`  
 \[入力\] をポイントする型。  これは [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスによって表されます。  
  
 `pPtrToTypeField`  
 \[入力\] **IDebugField の**  新しいオブジェクトによって表されるポインターを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)