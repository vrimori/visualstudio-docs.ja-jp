---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
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
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ドキュメントのコンテキストの指定された配列にこのドキュメントのコンテキストを比較します。  
  
## 構文  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### パラメーター  
 `compare`  
 \[入力\] 比較の種類を指定する [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) の列挙体の値。  
  
 `rgpDocContextSet`  
 \[入力\] 比較するドキュメントのコンテキストを表すこと [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) のオブジェクトの配列。  
  
 `dwDocContextSetLen`  
 \[入力\] 比較するドキュメントのコンテキストの配列の長さ。  
  
 `pdwDocContext`  
 \[入力\] 比較を満たす最初のドキュメントのコンテキストの `rgpDocContextSet` の配列にインデックスを返します。  
  
## 戻り値  
 一致が見つからなかった `S_OK` を返します。  一致が見つからなかった `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 配列に渡される [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) のオブジェクトは `IDebugDocumentContext2` のオブジェクトを実装する同じデバッグ エンジンで実装する必要が ; は比較は無効です。  
  
## 参照  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)