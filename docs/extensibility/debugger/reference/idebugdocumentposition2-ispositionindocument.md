---
title: "IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ドキュメントの場所が特定の文書に含まれているかどうかを判定します。  
  
## 構文  
  
```cpp#  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```c#  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### パラメーター  
 `pDoc`  
 \[入力\] 含むドキュメントの候補を表す [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) のオブジェクト。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) インターフェイスのブレークポイントの設定は本質的に使用されます。  ドキュメントとしてブレークポイントの位置ドキュメントがこの位置が含まれているかどうかを判断するために呼び出されます読み込まれます。  
  
## 参照  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)