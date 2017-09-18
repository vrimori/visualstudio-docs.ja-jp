---
title: "IDebugDocumentContext2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Seek"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Seek"
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ステートメントまたは行の指定した数値ドキュメントのコンテキストを移動します。  
  
## 構文  
  
```cpp#  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp#  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### パラメーター  
 `nCount`  
 \[入力\] ドキュメントのコンテキストに応じて前方に移動するステートメントまたは行の数。  
  
 `ppDocContext`  
 \[出力\] 新しい位置に [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) の新しいオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)